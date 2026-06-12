---
title: "xrandr custom resolution"
date: 2011-07-24
forum: General Help
---

### Post by SnakeMedia on 2011-07-24
Hello guys,

I would to change to bigger than current screen mode.

On my laptop display is current for 1366 x 768.
I will to add new size of next bigger resolution.. i need space of desktop.

I want to add : But it has problem it can not work.

I tell about size new resolution:
1366 * 1.5 = 2048 == 2048
768 * 1.5 = 1045 >= 1044
Depth: 32
Reflective: 60, 75 hz

It shows error:

```
xrandr --addmode LVDS 2048x1044_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  23
  Current serial number in output stream:  24

```

How do i fix this?

Thanks

---

### Post by CatKiller on 2011-07-24
It's incredibly unlikely that your display can do 2048x1045. You can't give your display more than twice as many pixels no matter how hard you wish.

---

### Post by realzippy on 2011-07-24
This will not work,your panel is too small.

---

### Post by SnakeMedia on 2011-07-24
> **CatKiller said:**
> It's incredibly unlikely that your display can do 2048x1045. You can't give your display more than twice as many pixels no matter how hard you wish. You have rights.. Thanks for tips! I do not think because Windows Version work nice better than Ubuntu :( Too Mac OS X can work bigger than current screen resolution :) I do not think becasue Mac OS X has screen resolution 1400x900 on my Laptop HP Compag 615. But Ubuntu can not :( Thanks 

regards, SnakeMedia

---

### Post by realzippy on 2011-07-24
> **CatKiller said:**
> You can't give your display more than twice as many pixels 

?
thought 
LCDs cannot go beyond their native resolution.

---

### Post by SnakeMedia on 2011-07-24
> **realzippy said:**
> This will not work,your panel is too small.
I understand Thanks...

PS: Edit: LCDs?? No That is LVDS :) Laptop Video Display :)

Thanks I know because possible native resolution on Mac OS X. Mac OS X can work more than Ubuntu. I know becasue Mac OS X i have been tested with Resolution because it is very smaller than Ubuntu. Windows can also more than small. Thanks i try buy new VGA on my computer :) Thanks for resolts!

regards SnakeMedia

---

### Post by CatKiller on 2011-07-24
> **SnakeMedia said:**
> screen resolution 1400x900 on my Laptop HP Compag 615.

The [specifications]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c01768607&lang=en&cc=us&taskId=101&prodSeriesId=3958411&prodTypeId=321957") for the Compaq 615 say that 1366x768 is the resolution of that display.

1400x900 is not a standard resolution. You might be thinking of 1440x900, but you're unlikely to be getting that either. If the pixels aren't there, they aren't there. It's possible that OS X is putting out a higher resolution and your monitor is scaling the image to its native resolution, but I doubt it.

EDIT: How are you running OS X on that thing, anyway?

---

### Post by CatKiller on 2011-07-24
> **realzippy said:**
> ?
thought 
LCDs cannot go beyond their native resolution.

That's exactly what I said. The display has the number of pixels that it has. SnakeMedia wants to magic 125% more pixels out of nowhere.

---

### Post by SnakeMedia on 2011-07-24
Thanks. I understand. Now i leave this. I think becasue it stopped bigger than resolution. Thanks!

It is ok... Thanks dear CatKiller and realzippy!

PS: It is possible because VBox is not native resolution when i am using scaling mode than it is very smaller than native resolution. Example: Native Resolution : 1366x768
VBox with Scaling Mode: 2048x1044

Do you think becasue it is faking by VirtualBox 4.1 ?

Regards SnakeMedia

---

### Post by CatKiller on 2011-07-24
> **SnakeMedia said:**
> Do you think becasue it is faking by VirtualBox 4.1 ?

If you're running it in a virtual machine then you can pretty much pretend that the resolution is anything and move the viewport around. Messy, though. There's a native-to-Ati option that does similar, called "bigdesktop" IIRC, which again lets you move the viewport around. You'll still only get to see 1366x768 of the pixels at any one time, though.

If you want twice as much Desktop space, why don't you try plugging in a monitor for a dual-monitor setup?

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

