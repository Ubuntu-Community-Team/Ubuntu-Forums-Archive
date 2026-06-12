---
title: "Font rendering in Firefox: Ubuntu 10.04 vs Windows 7"
date: 2010-07-13
forum: General Help
---

### Post by darkmaxa on 2010-07-13
I'm trying to tune up the font rendering in Ubuntu & Firefox 3.6, to look the same as in Windows 7 and Firefox 3.6.

[SIZE=4]**Example 01:**[/SIZE]
[IMG]http://i26.tinypic.com/k1778p.png[/IMG]



[SIZE=4]**Example 02:**[/SIZE]
[IMG]http://i28.tinypic.com/3449xr9.png[/IMG]



**Windows 7 settings:** all default
**Ubuntu 10.04 settings:** Smoothing-Greyscale, Hinting-Slight, Subpixel order-RGB, fonts in Firefox settings Times New Roman, Arial, Courier New

As you can see, fonts in Ubuntu look unsharp and too much bold (for my taste).

I also tried other combinations in Ubuntu font settings, as well as manual settings in ~/.fonts.conf file, but it didn't give better results than examples above.

**Did anyone manage to get font rendering in Ubuntu to be the same as in Windows?** How? Screenshot please! :)

I spent two days and I didn't manage to get result that comes out-of-the-box in Windows. :(

---

### Post by 289Shelby on 2010-07-13
Does this help?

[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

It's old but I think it's still valid.

---

### Post by timgood on 2010-07-13
I tried this which improved things a lot for me:

```
sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig
```

Then restart Firefox. Hope this helps.

---

### Post by darkmaxa on 2010-07-13
> **289Shelby said:**
> Does this help?

[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

It's old but I think it's still valid.


Nope. Now it's different, but still bad. Small non-bold fonts look like Windows font with "ClearType fonts" turned off, or in other words, anti-aliasing is turned off on small non-bold fonts, but on the other side bold fonts are still too much bold. 


[SIZE=3]**Screenshot:**[/SIZE]
[IMG]http://i32.tinypic.com/dc3a1e.png[/IMG]


If is someone managed to get good font renering in Firefox, please post here screenshot of some web page (google.com, ubuntuforums.org, facebook, ...), and precise instructions how to get this result.



> **timgood said:**
> I tried this which improved things a lot for me:

```
sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig
```Then restart Firefox. Hope this helps.

I do it already. Before this trick Firefox not even follow gnome font settings.

Can you, please, post some screenshots?

---

### Post by timgood on 2010-07-13
Screenshot as requested.

[IMG]http://eekageek.co.uk/uploads/images/Screenshot-%5Bubuntu%5D%20Font%20rendering%20in%20Firefox:%20Ubuntu%2010.04%20vs%20Windows%207%20-%20Ubuntu%20Forums%20-%20Mozilla%20Firefox.png[/IMG]

---

### Post by darkmaxa on 2010-07-13
Here is the same piece of web page (Win7 & FF 3.6), just for comparison:

[IMG]http://i27.tinypic.com/1iy937.png[/IMG]


I think the font rendering in Windows is significantly better or at least more pleasant to my eyes.

The question is whether it is possible to achieve this quality of render on Ubuntu and how?

---

### Post by negativ on 2010-07-13
You might try:

[http://www.infinality.net/files/local.conf](http://www.infinality.net/files/local.conf)

It's rather complex; you may (or may not) find it's worth your time to tweak the settings a bit.

Rename your ~/.fonts.conf to something else, and put the above file in /etc/fonts.  Of course, backup your existing local.conf.

X font rendering has been the source of rivers of tears.

---

### Post by darkmaxa on 2010-07-13
> **negativ said:**
> You might try:

X font rendering has been the source of rivers of tears.

If I continue to use Ubuntu, I'll have to visit the ophthalmologist soon. :(

Every tweak do something useful, but it is partial solution...

---

### Post by darkmaxa on 2010-07-13
[SIZE=2]This is the best result so far, but I'm not satisfied yet.[/SIZE]

**[SIZE=4]Screenshot:[/SIZE]**
[IMG]http://i32.tinypic.com/zl3wn8.png[/IMG]

[SIZE=2]I've achieved this by following [these instructions]("http://ubuntuforums.org/showthread.php?t=1483984&highlight=firefox+font+hardy").[/SIZE]

---

### Post by srus on 2011-09-01
Firefox doesn't follow Gnome's rules. It uses slight font hinting instead of full hinting:

sudo mv /etc/fonts/conf.d/10-hinting-slight.conf /etc/fonts/conf.d/10-hinting-slight.conf.backup

---

### Post by Mutikasa on 2011-12-19
Does this problem still persist in 10.10?

---

### Post by Rimdeker on 2012-06-25
I do not think it's a problem, per se. More of a feature and whether you prefer the Windows font rendering more than the Ubuntu one is a matter of opinion but in general the Windows font rendering is considered worse than the one of Ubuntu and Mac Os X

---

### Post by sffvba[e0rt on 2012-06-25
*Back to sleep **old **thread.*


404

---

