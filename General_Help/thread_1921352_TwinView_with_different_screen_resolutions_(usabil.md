---
title: "TwinView with different screen resolutions (usability)"
date: 2012-02-06
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-02-06
i figured out how to get panels on the second monitor :)
but since the primary screen is smaller than the second monitor i have dead space below my small screen is there a way i can make this off limits to the mouse/desktop icons?

if they were the same size/resolution i would just clone them

---

### Post by pqwoerituytrueiwoq on 2012-02-06
looks like seperate x server is what i want

is there a way to keep a mouse/keyboard from working on the other screen

eg for monitor A
hard wire mouse/keyboard
this mouse cant enter monitor B and this keyboard can't type on monitor B

eg for monitor B
wireless mouse /keyboard
this mouse cant enter monitor A and this keyboard can't type on monitor A

in a way this would be like 2 separate computers

---

### Post by pqwoerituytrueiwoq on 2012-02-07
i figured out a trick so i can keep the screen edge usage
if you create dead space between the screens by using both screens in a absolute position you get the edge back :)
but then you can't get to the other screen or at that is what the warning says but, you can still get there via terminal control of mouse

move to second monitor
[FONT=Courier New]xdotool mousemove --screen 1 800 450[/FONT]

move to first monitor
[FONT=Courier New]xdotool mousemove --screen 0 638 384[/FONT]

now you just have to create some panel buttons (or keyboard shortcuts) since all icons end up on the same screen :-|

now i need to get my compiz issues fixed automatically i was able to do it via the compiz fusion icon and a terminal command if i just know what command the icon runs when you click reload hopefully lucid will work (testing with laptop which has natty since the second monitor is not here yet)

---

