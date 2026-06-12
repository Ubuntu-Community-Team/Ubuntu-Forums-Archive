---
title: "No title/function bar in Firefox &amp; Evolution"
date: 2012-02-24
forum: General Help
---

### Post by wpshooter on 2012-02-24
Why is it in Ubuntu (using 11.04 - 32 bit) that on rare occasions when I open either Firefox or Evolution that the title / function bar is missing from the top of the window/dialogue ?

If I restart the computer they are then back to normal.

P.S. - The menu bar is always there, just the title bar is sometimes missing.

Thanks.

---

### Post by audiomick on 2012-02-24
Are you using Unity? I've had an 11.04 on my desktop for a couple of months, and I think Unity is still a bit flaky on that.

---

### Post by wpshooter on 2012-02-25
> **audiomick said:**
> Are you using Unity? I've had an 11.04 on my desktop for a couple of months, and I think Unity is still a bit flaky on that.

No, not using Unity and probably never will.

Thanks.

---

### Post by Plasma_NZ on 2012-02-25
sounds like compiz setting issue...

compiz - effects - window decorations

then look for "Decoration window"

make sure its on any, or u can specify which windows will have title-bar etc..

---

### Post by wpshooter on 2012-02-25
> **Plasma_NZ said:**
> sounds like compiz setting issue...

compiz - effects - window decorations

then look for "Decoration window"

make sure its on any, or u can specify which windows will have title-bar etc..

I don't think I  have any "Compiz" since I don't really know what it is, so I don't think that is what is causing the problem with title bars not showing up.

Thanks.

---

### Post by dcstar on 2012-02-26
> **wpshooter said:**
> **I don't think I  have any "Compiz"** since I don't really know what it is, so I don't think that is what is causing the problem with title bars not showing up.

Thanks.

Yes you do.

Select the "2D" of "No effects" option before you log in.

---

### Post by wpshooter on 2012-02-26
> **dcstar said:**
> Yes you do.

Select the "2D" of "No effects" option before you log in.

Thanks.

I assume that you are meaning the "**Ubuntu Classic - no effects**" choice that I am seeing ???

What is the difference between "**Ubuntu Classic & Ubuntu Classic - no**** effects**" ?

And why would having this set to **just** Ubuntu Classic have to do with the title bars not functioning correctly on a **random** basis ?

Thanks.

---

### Post by audiomick on 2012-02-26
As I understand it, compiz is responsible for all the flashy effects on your desktop. 
Selecting "no effects" puts you in a mode that doesn't use any 3D effects on the desktop. This is easier on your resources, and necessary if you don't have a 3D capable driver for your video card.

If you select "classic" without specifying "no effects", I believe the desktop environment will be trying to use 3D effects. If there is something shaky there, then you might see the sort of intermíttent problem you are describing.

Try booting in with no effects and see how it behaves. It should at least help narrow down where your problem is coming from.

---

