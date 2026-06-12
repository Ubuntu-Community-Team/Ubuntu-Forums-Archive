---
title: "Command for inserting symbols? OR Custom keyboard layout"
date: 2010-02-24
forum: General Help
---

### Post by manfrom3004 on 2010-02-24
Is there a way to set up a custom keyboard layout? (ex: set q to the f key, etc.) I have looked around, but have been unable to find one. 
If there isn't one, then a (basically) equivalent solution for me would be to map some of the symbols I need (ex: &#916;x,&#931;,ect.) to ctrl-/,ctrl-., ect. through keyboard shortcuts. The problem I run into here is that I do not know of any commands that paste a specific symbol into the focused text input area. Does anyone know of one?
Any help would be appreciated. Thank you in advance.

---

### Post by drink_stir on 2010-02-25
i just searched this on google the other day.  and guess where it brought me... u guessed it... right back here ---->[http://ubuntuforums.org/showthread.php?t=125107](http://ubuntuforums.org/showthread.php?t=125107)

---

### Post by tom7 on 2010-03-02
The simplest way is to modify keyboard layout in /usr/share/X11/xkb/symbols. The rest depends on which keyboard layout you use and what do you want to change. I have made successful modifications in Ubuntu 9.10.

---

### Post by asmoore82 on 2010-03-02
Have you checked out "Applications -> Accessories -> Character Map" ?

You might be able to use it in combination with the "Glipper" clipboard manager
to meet your needs.

---

### Post by ernieg92 on 2012-12-01
I realize this is an older forum, but I´ve spent HOURS searching for an answer to this question.

I´m running Kubuntu 12.10.  I have modified the ´international with dead keys´ section of the ¨us¨ file in /usr/share/X11/xkb/symbols/.  My desire is/was to re-arrange some of the level 3/4 keys (and delete some) so that I can insert special characters (¢ ° £ etc).  However, KDE doesn´t recognize the changed order on some keys and completely ignores the other keys (for example, it uses the acute (´) where it says ¨apostrophe¨ (') in the file.

Is there some other file I should be modifying to make my desired changes?

Thanks!

---

### Post by rnerwein on 2012-12-02
> **ernieg92 said:**
> I realize this is an older forum, but I´ve spent HOURS searching for an answer to this question.

I´m running Kubuntu 12.10.  I have modified the ´international with dead keys´ section of the ¨us¨ file in /usr/share/X11/xkb/symbols/.  My desire is/was to re-arrange some of the level 3/4 keys (and delete some) so that I can insert special characters (¢ ° £ etc).  However, KDE doesn´t recognize the changed order on some keys and completely ignores the other keys (for example, it uses the acute (´) where it says ¨apostrophe¨ (') in the file.

Is there some other file I should be modifying to make my desired changes?

Thanks!
hello
here is a not so comfortable way to make the changes - but !!! this work on all unix/linux systems running X.
1. open a terminal
2. type: xev  (a liitle window will be open and when you enter any keystroke the code  
     will be shown on the command line
3. type: xmodmap -pke >  your_new_modmap.txt ( name of the file dosen't matter)
4. now you can modify your_new_modmap.txt with a text editor to your belongs.
5. type: xmodmap your_new_modmap.txt
--> you can run point 5 in a shell script: e.g. with your_new_modmap.txt or if you want
     the old values back run xmodmap with a non modified file (given from xmodmap -pke)
much fun

---

### Post by wildmanne39 on 2012-12-02
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

