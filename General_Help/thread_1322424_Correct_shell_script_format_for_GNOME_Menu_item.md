---
title: "Correct shell script format for GNOME Menu item?"
date: 2009-11-10
forum: General Help
---

### Post by ramjet_1953 on 2009-11-10
Hi, Guys!

I've searched around and still can't find a solution to my problem.

I want to put [COLOR="Blue"]Storybook[/COLOR] into my menu, but I can't seem to crack it.

It is a shell script and to execute it you type this into a terminal:

 ```
./storybook.sh
```

I have tried the following [COLOR="Blue"]command lines[/COLOR] in menu editor with no success:

1. ```
sh /home/roger/Storybook/storybook.sh
```

2. ```
sh /home/roger/Storybook/./storybook.sh
```

3. ```
/home/roger/Storybook/./storybook.sh
```

Just typing the command ./storybook.sh in a terminal works.

Any ideas???

Reagrds,
Roger:D

---

### Post by Giblet5 on 2009-11-10
Try ```
bash /home/roger/Storybook/storybook.sh
```

or

```
/home/roger/Storybook/storybook.sh
```


It's probably missing a shell specifier at the top eg ```
#!/bin/bash
...
```

From a terminal, you'll execute it with bash...so that top example will probably work.

---

### Post by mo.reina on 2009-11-10
you have to create a text file with the following fields.

```
[Desktop Entry]
Name=XChat IRC
Comment=Chat with other people using Internet Relay Chat
Exec=xchat
Icon=xchat
Terminal=false
Type=Application
Categories=Network;
StartupNotify=true

```

exec is the command you would type in the terminal to get the script to run
categories is the category in the gnome menu: applications, network, office, internet, etc.

save it under **filename**.desktop and put it in /usr/share/applications.  gnome menu should now have the item under the appropriate category

---

### Post by Giblet5 on 2009-11-10
> **mo.reina said:**
> **[COLOR="DarkRed"]you have to create a text file with the following fields[/COLOR]**.

```
[Desktop Entry]
Name=XChat IRC
Comment=Chat with other people using Internet Relay Chat
Exec=xchat
Icon=xchat
Terminal=false
Type=Application
Categories=Network;
StartupNotify=true

```

exec is the command you would type in the terminal to get the script to run
categories is the category in the gnome menu: applications, network, office, internet, etc.

save it under **filename**.desktop and put it in /usr/share/applications.  gnome menu should now have the item under the appropriate category

And you have to use vi in ex mode, or an awk script, to create it.... :D

No. That highlighted part is not true. That's how you and I do it, but there are other ways. GUIer ways.

He was using the menu editor. It creates the .desktop entry for you from gui text fields.

---

### Post by mo.reina on 2009-11-10
there are other ways?](*,) i've wasted all those hours!!

i'll go with awk option, it sounds cooler :cool:

seriously though, i must not have been paying attention.  so what's the problem?

---

### Post by Giblet5 on 2009-11-10
> **mo.reina said:**
> there are other ways?](*,) i've wasted all those hours!!

i'll go with awk option, it sounds cooler :cool:

seriously though, i must not have been paying attention.  so what's the problem?

Executing a shell script (that I don't think OP wrote) does nothing, but works from the shell.

He tried using 'sh scriptname', I suggested using 'bash scriptname', and OP has been silent since. I suspect OP departed the thread the instant that it worked.

A lot of people do that. I have 1,275 tabs open in firefox as a result. ;)

---

### Post by JBAlaska on 2009-11-10
> **Giblet5 said:**
> A lot of people do that. I have 1,275 tabs open in firefox as a result. ;)

I hate when that happens LOL.

[COLOR="blue"]&#729;u&#653;op &#477;p&#305;sdn &#633;o&#647;&#305;uo&#623; &#654;&#623; p&#477;u&#633;n&#647; &#647;sn&#638; I &#647;nq&#729;&#729;&#623;&#477;&#643;qo&#633;d &#647;&#592;&#613;&#647; &#477;&#652;&#592;&#613; p&#305;p I[/COLOR]

---

### Post by mo.reina on 2009-11-11
lol you gotta love it

---

### Post by ramjet_1953 on 2009-11-12
I've tried all of the above, but still no luck.

Also had a difficult job of getting rid of the .desktop files when they were created.

With that suffix, they seem to need a higher level of permission than sudo gives.

Regards,
Roger:D

---

### Post by GrimJack on 2010-02-07
I am also trying to get Storybook to launch from the Gnome menu and have had no luck with any of the above directions.

Here's the program: [http://storybook.intertec.ch/joomla/](http://storybook.intertec.ch/joomla/)

The user just extracts the program files from the .tar.gz archive downloaded from that site into the directory of their choice under /home/user, then runs the program by opening a terminal in that directory and typing ```
./storybook.sh
```

No sudo, nothing other than user permissions are used. The program is written in Java, FWIW.

Anyone?

---

### Post by munkybut on 2010-10-10
Wow.  I have had this same problem several times now with several different files, and it just so happens this time I am also trying to use Storybook.  The storybook.sh file's permissions are -rwxr-xr-x.  If I run /home/munkybut/storybook/storybook.sh from nautilus it runs fine.  If I run the file from the terminal as $ /home/munkybut/storybook/storybook.sh (or just ./storybook.sh from the parent directory) it runs fine.

The problem seems to only occur when you add the file to the GNOME Menu.  I have tried to run the application through the GNOME Menu with the following and none worked:
Command: /home/munkybut/storybook/storybook.sh
Command: sh /home/munkybut/storybook/storybook.sh
Command: bash /home/munkybut/storybook/storybook.sh

The script consists of the following (again: this works fine directly from the terminal):

[I]#!/bin/bash
echo "starting ..."
java -Xmx256m -jar lib/storybook.jar
echo "done."[/I]

I read somewhere that sometimes files have issues when they refer to a relative pathname.  I have edited the script so that line 3 is:
*LINE 3: java -XMx256m -jar /home/munkybut/storybook/lib/storybook.jar*

And also I have tried adding a new line before line 3 that reads as:
*LINE 3: cd /home/munkybut/storybook*
*LINE 4: java -Xmx256m -jar lib/storybook.jar*

None of these have worked either.  I have had this happen with several applications now, and if someone could enlighten me, I'd be quite happy.

-Thanks!

---

### Post by BoredSilly on 2010-10-10
java environment variable perhaps?
What i'd do in the script is add: env > /tmp/tmpenv

run it successfully and copy tmpenv sideways then run again from the menu and look for any differences between the 2 files.

---

### Post by andrewn2000 on 2010-12-15
[http://ubuntuforums.org/showthread.php?t=1289534](http://ubuntuforums.org/showthread.php?t=1289534)

This worked for me.

Andy

---

### Post by GrimJack on 2011-01-13
Seconded. This also worked for me. (Thanks!)

I created a new text file called [SIZE="2"][FONT="Courier New"]storybooklaunch.sh[/FONT][/SIZE] and put this in it:

```
cd /home/grimjack/storybook/
sh storybook.sh
```

I put this file in [FONT="Courier New"][SIZE="2"]/home/grimjack/storybook/[/SIZE][/FONT]

Then I created a launcher in Gnome that points to:

```
sh /home/grimjack/storybook/storybooklaunch.sh
```

And changed the "Application" drop-down to "Application in Terminal".

When launched from the Gnome menu, a terminal window opens and the expected startup messages displayed, then the Storybook GUI opens.

Hope this helps.

---

### Post by legendbb on 2012-02-17
I know the problem was resolved long time ago.

Just because when I encounter the same issue, don't get much from a good search. But this thread definitely solved my issue in 2012. Add and witness record here to help with others.

In the menu command line: bash ${absolute_path}/your_script.sh

Thanks

---

