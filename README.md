# assignment2-jadhav

# Preethi Jadhav

### Hyderabad

The place I like the most is **Hyderabad**.I have been living in this city since birth.So it is a very dear place to me.I have completed my education here.**And most of my friends live in Hyderabad as well.**

---
## Directions to Hyderabad from Maryville

To travel to Hyderabad from Maryville.
1. Take a taxi/car from Maryville to neareast International Airport (Kansas).
2. Your flight may be direct or indirect.
3. If you land in Delhi,India or Mumbai,India
4. You can take another domestic flight to Hyderabad.
5. Or you can also travel to Hyderabad by road from these cities.

Things to carry to Hyderabad for maximum enjyoment.
* In winters 
    * Good to carry warm clothes 
    * Jackets
* In Rainy
    * We need to carry an Umbrella.
    * Rain boots
    * Rain Coats
* In summers 
    * Sun Glasses 
    * Sunscreen 
    * Hats/Caps

[link to Aboutme](AboutMe.md)

---

## Food and Drinks to Try!

This table below shows food and drinks you can try at diffrent restaurants. It also gives the information about the amount you can expect to spend on the items and the resturants/locations they are available at .

| Food/Drink  | Location | Amount  | 
| ------------- | ------------- | ------------- | 
| McSpicy Ckicken Burger  | McDonald's | 1.99 $  | 
| Mocha Caramel Coffee  | Starbucks  | 3.00 $ | 
| Banana Bread  | Starbucks  | 2.80 $  | 
| Vanilla Shake  | McDonald's |2.50 $  | 

---
## Quotes 

> The only thing you have to fear is fear itself. *- F.D Roosevelt*

> You must be the change you wish to see in the world. *- Mahatma Gandhi*

---

## Code Fencing - Convex Hull construction using Graham's Scan

> Graham's scan is a method of finding the convex hull of a finite set of points in the plane with time complexity O(n log n). It is named after Ronald Graham, who published the original algorithm in 1972. The algorithm finds all vertices of the convex hull ordered along its boundary. It uses a stack to detect and remove concavities in the boundary efficiently.

[link to Description Source](https://en.wikipedia.org/wiki/Graham_scan)

```
struct pt {
    double x, y;
};

bool cmp(pt a, pt b) {
    return a.x < b.x || (a.x == b.x && a.y < b.y);
}

bool cw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) < 0;
}

bool ccw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) > 0;
}

void convex_hull(vector<pt>& a) {
    if (a.size() == 1)
        return;

    sort(a.begin(), a.end(), &cmp);
    pt p1 = a[0], p2 = a.back();
    vector<pt> up, down;
    up.push_back(p1);
    down.push_back(p1);
    for (int i = 1; i < (int)a.size(); i++) {
        if (i == a.size() - 1 || cw(p1, a[i], p2)) {
            while (up.size() >= 2 && !cw(up[up.size()-2], up[up.size()-1], a[i]))
                up.pop_back();
            up.push_back(a[i]);
        }
        if (i == a.size() - 1 || ccw(p1, a[i], p2)) {
            while(down.size() >= 2 && !ccw(down[down.size()-2], down[down.size()-1], a[i]))
                down.pop_back();
            down.push_back(a[i]);
        }
    }

    a.clear();
    for (int i = 0; i < (int)up.size(); i++)
        a.push_back(up[i]);
    for (int i = down.size() - 2; i > 0; i--)
        a.push_back(down[i]);
}

```
[link to Algorithm Source](https://cp-algorithms.com/geometry/grahams-scan-convex-hull.html)