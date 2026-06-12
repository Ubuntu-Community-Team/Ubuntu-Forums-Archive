---
title: "script or macro for repetitive tasks"
date: 2010-02-18
forum: General Help
---

### Post by rcragun on 2010-02-18
I have several things I do regularly in Ubuntu for which I would like to have a single button, shortcut, or keyboard combination.  I've been using Ubuntu for a year now (crossed over from Windows) and, while I'm pretty good with computers, I've never really done any programming beyond HTML (so, no real programming).  But I figure there has to be easier ways to do the following:

1) Due to repetitive stress problems, I have taught myself to use a mouse both left and right handed.  My mouse on my desktop at home is set for right-handed use and it doesn't change.  However, at work I use a laptop with a docking station.  The mouse on the docking station is set to be left-handed, mixing up which hand I use to minimize repetitive movements.  But when I undock my laptop (which is several times a day), I switch the mouse settings back to right handed as the keypad is awkward to manage left-handed.  Obviously switching from right-handed to left-handed isn't that hard: System -> Preferences -> Mouse.  To speed things up, I created a shortcut to the Mouse menu on my top panel.  But it still requires 3 clicks to change the mouse setting from right-handed to left-handed.  I'd like to make it a single-click affair - I hit a button or some keyboard combination and my mouse changes from right-handed to left-handed.  Any suggestions on how to do that?

2) I'm a college professor (obviously not in computer science).  The reason I undock and redock my laptop multiple times during the day is because I am teaching classes and I use my laptop to present powerpoints and multimedia to my classes.  Whenever I dock or undock, not only do I have to switch the mouse settings, but I have to change the monitor settings.  Attached to my laptop dock is an external monitor, which gives me dual monitors when docked.  Changing the monitor settings isn't that hard, of course (System -> Preferences -> Display), and I've even added the "displays" icon to the panel, which means it's relatively quick to change my displays.  But it still requires several clicks.  I click the icon in my panel, it brings up the Display Preferences window.  I then have to select the external monitor, change the resolution settings (Ubuntu can only handle certain resolutions, particularly with my crappy laptop), position the external monitor correctly, then hit apply.  I have to do this every time I dock, every time I am going to undock, every time I connect the external projector, and every time I am going to disconnect from the external projector.  Since the projector settings and the external monitor settings are the same every time, it would be nice if I had a single button shortcut that simply changed my display preferences to whatever I have connected: (1) external monitor when docked, (2) external projector for classroom presentations, and (3) no external monitor when not docked.  Any suggestions on how to make this happen?

3) On my desktop computer at home I have dual monitors.  I have set Songbird to load automatically when I start my computer, but it always starts on the left-hand monitor and I like it on the right-hand monitor, which means I have to move it every time I startup my computer (usually once a day in the morning).  Is there something I can change in the launch command in System -> Preferences -> Startup Applications to make the Songbird window move to the right monitor instead of the left one?

Thanks in advance for any suggestions.

---

### Post by jamesisin on 2010-02-18
Welcome to the forums.

I would split your thread into three well crafted (and well titled) threads.  You will be much more likely to get the kind of specific help you'll need.

I did have a thought about your third issue.  I suppose Sb is firing up on your main monitor?  If you tell Sb to open on the other monitor (and perhaps it's possible) that may lead to troubles if you open Sb while not docked.  Just a thought.

---

### Post by DaithiF on 2010-02-18
Hi, for making the mouse left or handed you can use gconftool.  I don't know if its part of the default install or not, if you don't have it then install package gconf2.

Then, this command will make mouse left-handed:
```
gconftool -s /desktop/gnome/peripherals/mouse/left_handed -t bool true
```
and this will revert it to right-handed:
```
gconftool -s /desktop/gnome/peripherals/mouse/left_handed -t bool false

```
So you could create a pair of custom launchers in your panel with these as the commands.

---

### Post by jamesisin on 2010-02-18
He could probably do a test (if true) to determine handedness.  In which case he could put both of those statements (if and else) into a single script and use a launcher to run that script.

---

### Post by DaithiF on 2010-02-18
and for the monitor / resolution question, take a look at the xrandr utility.
this article may help: [http://solnyshok.blogspot.com/2009/11/switch-between-laptop-lcd-and-external.html](http://solnyshok.blogspot.com/2009/11/switch-between-laptop-lcd-and-external.html)

---

### Post by pi/roman on 2010-02-18
like this

> switchmb=$(gconftool -g /desktop/gnome/peripherals/mouse/left_handed)
if [ $switchmb = "false" ];  then
    gconftool -s /desktop/gnome/peripherals/mouse/left_handed -t bool "true"
else
    gconftool -s /desktop/gnome/peripherals/mouse/left_handed -t bool "false"
fi
exit 0
make it executable place it in /usr/bin and use gnome-keybinding-properties to tie it to a hotkey.

---

### Post by DaithiF on 2010-02-18
or slightly shorter:
```
current_setting=$(gconftool -g /desktop/gnome/peripherals/mouse/left_handed)
$current_setting && new_setting=false || new_setting=true
gconftool -s /desktop/gnome/peripherals/mouse/left_handed -t bool $new_setting

```

nice avatar pi/roman, who is that -- nero?

---

### Post by rcragun on 2010-02-18
> **DaithiF said:**
> Hi, for making the mouse left or handed you can use gconftool. I don't know if its part of the default install or not, if you don't have it then install package gconf2.

Then, this command will make mouse left-handed:
```
gconftool -s /desktop/gnome/peripherals/mouse/left_handed -t bool true
```and this will revert it to right-handed:
```
gconftool -s /desktop/gnome/peripherals/mouse/left_handed -t bool false

```So you could create a pair of custom launchers in your panel with these as the commands.



This worked.  Thank you!

Now trying the if/then approach.

---

### Post by pi/roman on 2010-02-18
> nice avatar pi/roman, who is that -- nero?

Yep, thanx, and thanx for teaching me some new scripting methods.

---

### Post by rcragun on 2010-02-18
> **DaithiF said:**
> or slightly shorter:
```
current_setting=$(gconftool -g /desktop/gnome/peripherals/mouse/left_handed)
$current_setting && new_setting=false || new_setting=true
gconftool -s /desktop/gnome/peripherals/mouse/left_handed -t bool $new_setting

```nice avatar pi/roman, who is that -- nero?


This worked as well.  I opened a text file using sudo gedit /usr/bin/mouse_switch and  copied the code as is and pasted it into the text file.  I then CHMOD'd mouse_switch and used keyboard bindings (CTRL+SHIFT+M) to attach it to a keyboard binding.  et voila, I have a keyboard shortcut to switch my mouse configuration.

So nice!!!  Thank you!!!

(Now I just have to figure out how it works...)

---

### Post by diesch on 2010-02-18
[http://sikuli.csail.mit.edu/](http://sikuli.csail.mit.edu/) loks quite nice (but I didn't try it so far)

---

### Post by jamesisin on 2010-02-18
I am just learning BASH but I don't quite see how this one works.

This line:

```
current_setting=$(gconftool -g /desktop/gnome/peripherals/mouse/left_handed)
```

clearly makes the true/false test.  The variable $current_setting is set to either true or false.

Then this line:

```
$current_setting && new_setting=false || new_setting=true
```

makes the if/then decision.  What I'm not clear on is what about this makes it "change to the other one"?

---

### Post by DaithiF on 2010-02-18
> **jamesisin said:**
> I am just learning BASH but I don't quite see how this one works.

This line:

```
current_setting=$(gconftool -g /desktop/gnome/peripherals/mouse/left_handed)
```clearly makes the true/false test.  The variable $current_setting is set to either true or false.

Then this line:

```
$current_setting && new_setting=false || new_setting=true
```makes the if/then decision.  What I'm not clear on is what about this makes it "change to the other one"?

the use of && (logical and) and || (logical or) is a fairly common way of linking commands together when you want them to depend on each other in some way.

A && B || C means evaluate expression A and do B if the result is true or do C if the result is false.  This makes sense more when you think of them in pairs ... so taking A && B first ... if the result of A is False, then there is no way that False AND <something else> can be true, and so the second expression is not evaluated.  So its a way of chaining 2 commands or expressions when you only want the second to run if the first succeeds (or evaluates to True).

Combining 2 commands with || (logical or) has the effect of only running the second command if the first fails (or evaluates to false).  If you have  X || Y, this means X OR Y ... and if X is true, then X OR Y has to be true, and so there is no need to evaluate Y.

Not sure if that helps, probably clear as mud ... explanations perhaps not my strong suit :)

---

### Post by jamesisin on 2010-02-18
Perfect explanation (two philosophy degress here).

Thanks.

(Can't say others will understand, but I do.)

---

### Post by diesch on 2010-02-18
Better use
 
```
if [ "$current_setting" = 'false' ]; then
  gconftool -s /desktop/gnome/peripherals/mouse/left_handed -t bool true
else
  gconftool -s /desktop/gnome/peripherals/mouse/left_handed -t bool false
fi
```


```
$current_setting && new_setting=false || new_setting=true
```
is a bit ugly in shell code and may lead to unexpected results as it runs the value of *$current_setting* as a shell command.

---

### Post by jamesisin on 2010-02-18
What is 'it' and why would it run $current_setting as a command?

---

### Post by diesch on 2010-02-18
```
$current_setting && new_setting=false || new_setting=true
```
means "run *$current_setting* as a shell command. If its exit code is 0 run *new_setting=false* otherwise run *new_setting=true*"

---

### Post by DaithiF on 2010-02-18
> ```
$current_setting && new_setting=false || new_setting=true
```is a bit ugly in shell code
You're right, its a bit ugly, but i think it maybe makes up for that in educational value -- which for a forum post is part of the game ... it throws out logical operators and the existence of the shell true / false commands -- maybe useful to someone who hasn't seen them before.

> and may lead to unexpected results as it runs the value of *$current_setting* as a shell command.  since $current_setting is the result of a gconftool query of a boolean attribute, its only going to get back true or false, so its fairly safe.  For a throwaway script like this its ok but yes, you wouldn't write code like this for landing the mars rover.

---

### Post by DaithiF on 2010-02-18
> **jamesisin said:**
> What is 'it' and why would it run $current_setting as a command?
```
man true
man false

```
though in reality true and false are bash builtins too, so its actually the bash builtin you are running rather than the external command /bin/true or /bin/false

ps, in particular i like this sentence:
```
$ man false
NAME
       false - do nothing, unsuccessfully

```

---

### Post by rcragun on 2010-02-18
> **DaithiF said:**
> and for the monitor / resolution question, take a look at the xrandr utility.
this article may help: [http://solnyshok.blogspot.com/2009/11/switch-between-laptop-lcd-and-external.html](http://solnyshok.blogspot.com/2009/11/switch-between-laptop-lcd-and-external.html)


I just tried this docked and it worked, though it was a little tricky.  Here are the commands I used:
To turn on dual monitors with my external monitor to the left of my laptop
Shift+Ctrl+D = xrandr --output VGA --auto --left-of LVDS --auto

Note: I originally tried reversing the order (i.e., xrandr --output LVDS --auto --right-of VGA --auto) but it didn't work.  Not sure if it only does "left-of", but that seemed weird.

Shift+Ctrl+N = xrandr --output VGA --off --output LVDS --auto

Ubuntu forums rock!

Anyone have any thoughts on positioning a window on dual monitors on boot up?

---

### Post by DaithiF on 2010-02-18
> **rcragun said:**
> Anyone have any thoughts on positioning a window on dual monitors on boot up?
Not sure about these, as I've no experience with dual monitors, but a couple of things you could try would be:
(a) if you are running compiz window manager, i believe there are settings there for remembering window positions -- i don't know if this will extend to dual monitors though
(b) if you're using metacity window manager, you could take a look at the wmctrl utility, it allows you to position windows from the command line, so you could have a wrapper script for songbird that first launches the app, and then runs a wmctrl command to position it where you want.  Again though, i don't know if it will work with dual monitors

---

### Post by DaithiF on 2010-02-18
theres also devilspie, see [https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie), though I'm more of a wmctrl guy myself.

---

### Post by diesch on 2010-02-18
> **DaithiF said:**
> You're right, its a bit ugly, but i think it maybe makes up for that in educational value -- which for a forum post is part of the game ... it throws out logical operators and the existence of the shell true / false commands -- maybe useful to someone who hasn't seen them before.


I see your point but I think it's more important to teach good style.

> **DaithiF said:**
> 
  since $current_setting is the result of a gconftool query of a boolean attribute, its only going to get back true or false, so its fairly safe.  


Errors like
```
gconftool -s /desktop/gnome/peripherals/mouse/left_handed -t string yes
```
are happening.

> **DaithiF said:**
> 
For a throwaway script like this its ok but yes, you wouldn't write code like this for landing the mars rover.

Throwaway scripts often have a tendency to get transformed into production code over time...

---

### Post by jamesisin on 2010-02-18
I'm still not seeing the danger here.

I can set a variable to a command and then run that variable (an by proxy the command) but I don't see how including it in this script runs any risk.  The variable is not exported and so should *only* be available within the script.

This works:

```
testme=ls | $testme
```

But close your terminal and try running that command again ($testme) will return nothing.

---

### Post by DaithiF on 2010-02-18
i suppose diesch's point is that someone could insert a malicious command as the value of the gconf key, e.g.:
gconftool -s /deliberately/not/a/real/path -t string "rm -rf ~/*"
so that naively executing the value you get back isn't a great idea.

so ```
[[ $current_setting == "true" ]] && new_setting="false" || new_setting="true"
```would be better, or indeed the if else method.

---

### Post by jamesisin on 2010-02-18
I see.  So the == means if and only if... what does the double-brackets signify?

---

### Post by DaithiF on 2010-02-18
== means 'equals', as in, does whats on the left equal whats on the right.

double brackets achieve the same as single brackets, ie, they perform a test of what is contained within, returning either true or false based on the result of the test.  The difference is that single bracket is an external command (located at /usr/bin/[), whereas [[ is builtin to the shell.  Arguably [[ is better though its not going to work in some older shells.

---

### Post by diesch on 2010-02-18
> **DaithiF said:**
> i suppose diesch's point is that someone could insert a malicious command as the value of the gconf key, e.g.:
gconftool -s /deliberately/not/a/real/path -s string "rm -rf ~/*"
so that naively executing the value you get back isn't a great idea.


It's not so much about an attacker but just some error, like setting a value to the string "yes" instead of the boolean "true" (*yes* is a shell command that prints "y" forever so the script would never switch the mouse but just waste CPU time in this case).

---

### Post by jamesisin on 2010-02-18
That's what I guessed.  Like parentheses in an algebraic equation.

Thanks again.

---

### Post by diesch on 2010-02-18
> **DaithiF said:**
> == means 'equals', as in, does whats on the left equal whats on the right.


== means 'value on the left side matches pattern on the right side'.  Parts of the right side that are quoted are interpreted as strings, not patterns.

In this case it doesn't make a difference as to right side is quoted and doesn't any special characters.


> **DaithiF said:**
> 
double brackets achieve the same as single brackets, ie, they perform a test of what is contained within, returning either true or false based on the result of the test.  The difference is that single bracket is an external command (located at /usr/bin/[), whereas [[ is builtin to the shell.  Arguably [[ is better though its not going to work in some older shells.

[ is a builtin in most shells (including bash und dash). The difference between [ and [[ is that word  splitting  and pathname expansion are not performed with [[ so you don't need to protect variables by "...". 

I usually prefer [ as it's working with any POSIX compliant shell.

---

### Post by rcragun on 2010-02-19
> **DaithiF said:**
> and for the monitor / resolution question, take a look at the xrandr utility.
this article may help: [http://solnyshok.blogspot.com/2009/11/switch-between-laptop-lcd-and-external.html](http://solnyshok.blogspot.com/2009/11/switch-between-laptop-lcd-and-external.html)

So, this worked when the resolutions were set to "auto" (as noted in an earlier response), but when I try to set the resolutions of the outputs, I'm not having any luck.  Here's what I'm doing:

I'm trying to hook up my laptop to an external projector.  The default resolution on my laptop is 1024x768.  However, the default resolution on the projector is 1368x768 (it's a weird resolution).  I want the projector to display the same resolution as my laptop - so both are 1024x768.  However, when I try to set up the xrandr shortcut, I can't get the projector's resolution to 1024x768. 

Here's the code I have been using, but for some reason it sets both my laptop and the projector to 1368x768:

xrandr --output VGA -s 1024/1024x768 --same-as LVDS --auto

I've tried about 30 different combinations, but none of them seem to work.  Thoughts on what I'm doing wrong?

---

### Post by diesch on 2010-02-19
Does the projector support 1024x768?

---

