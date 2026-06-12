---
title: "Screenlets problems"
date: 2011-12-18
forum: General Help
---

### Post by Silentwave on 2011-12-18
Hi, I have screenlets installed on my Ubuntu with two widgets always open.
But when I restart pc the widgets change position in the desktop also if I block it in "Widget Options" , so every time I reboot i have to put it back.
How can I resolve this problem?

Sorry for my bad english
Bye

---

### Post by thaelim on 2011-12-18
So you have already tried checking the "Lock position" option in the screenlet settings?

I'm afraid Screenlets is a rather buggy piece of software - the few I have played with had many bugs and annoyances. There might not be any way of fixing your problem short of hacking the code yourself.

---

### Post by Silentwave on 2011-12-18
> **thaelim said:**
> So you have already tried checking the "Lock position" option in the screenlet settings?

I'm afraid Screenlets is a rather buggy piece of software - the few I have played with had many bugs and annoyances. There might not be any way of fixing your problem short of hacking the code yourself.
Yes, I try the lock position, but the problem persists.
I think that if I delay the opening of screenlets after login the problem perhaps disappears.
Does anyone know how to delay the opening of a demon?

Thanks, bye

---

### Post by Guido Tabbernuk on 2011-12-18
> **thaelim said:**
> I'm afraid Screenlets is a rather buggy piece of software - the few I have played with had many bugs and annoyances. There might not be any way of fixing your problem short of hacking the code yourself.
This is rather uninformed. Please see [https://bugs.launchpad.net/screenlets/+bug/885322](https://bugs.launchpad.net/screenlets/+bug/885322)

So you have found some bugs? Have you reported any of them? You say one has to hack the source code oneself? So you have done it? But have you proposed any patches?

---

### Post by thaelim on 2011-12-19
> **Guido Tabbernuk said:**
> This is rather uninformed. Please see [https://bugs.launchpad.net/screenlets/+bug/885322](https://bugs.launchpad.net/screenlets/+bug/885322)

So you have found some bugs? Have you reported any of them? You say one has to hack the source code oneself? So you have done it? But have you proposed any patches?

Suffice it to say I'm a Python veteran of 10 years and I can tell the difference between good and poor quality code. I have also tried screenlets for many months myself (and modified them for my own purposes). 

There is a reason there is a Conky thread in the Cafe with nearly 19,000 posts and over 4 million views, and no similarly popular screenlets thread.

---

### Post by Guido Tabbernuk on 2011-12-19
> **thaelim said:**
> Suffice it to say I'm a Python veteran of 10 years and I can tell the difference between good and poor quality code. I have also tried screenlets for many months myself (and modified them for my own purposes).

No, that does not suffice at all!

Well, I don't claim the quality of the code is excellent, more like the opposite, it's full of functions written by people with different skills during different times and there has been quite poor management etc.

But this doesn't mean the code as such is buggy and one has to hack source code oneself in order to get it working. But this is exactly what you said at the beginning. Screenlets framework runs and does it pretty decently in recent Ubuntu versions. If individual screenlets by different authors are not updated, this is the problem of corresponding authors, not the Screenlets framework.

There is a huge difference between being "buggy" for a common user and being of a "poor quality" from developer's perspective. Usually, when one speaks about bugs, these are things that break functionality. I strongly claim that functionality of Screenlets is quite decent and this was the main reason I opposed your bashing comments.

> **thaelim said:**
> There is a reason there is a Conky thread in the Cafe with nearly 19,000 posts and over 4 million views, and no similarly popular screenlets thread.

Yes, Conky is a fun to configure thing for the kids, of course it has massive amount of posts already because of that. Screenlets is more like "install and start using immediately" type of software, why should it be discussed the way Conky is, anyway?

---

### Post by Silentwave on 2011-12-19
> **Guido Tabbernuk said:**
> This is rather uninformed. Please see [https://bugs.launchpad.net/screenlets/+bug/885322](https://bugs.launchpad.net/screenlets/+bug/885322)

So you have found some bugs? Have you reported any of them? You say one has to hack the source code oneself? So you have done it? But have you proposed any patches?
Ok, I read the bug, and in fact the solution is to delay screenlets on start with this:

```

                 Oh, probably you cannot just put "sleep 5 &&" there in the middle, but have to do it like
    Exec= bash -c "sleep 5 && python -u /usr/share/screenlets/screenlets-pack-basic/Lipik/LipikScreenlet.py"

```


   so what should I do? run Exec= bash -c "sleep 5 && python -u /usr/share/screenlets/screenlets-pack-basic/Lipik/LipikScreenlet.py" in the Terminal?


Thanks
Bye

---

### Post by stinkeye on 2011-12-19
> **Silentwave said:**
> Ok, I read the bug, and in fact the solution is to delay screenlets on start with this:

```

                 Oh, probably you cannot just put "sleep 5 &&" there in the middle, but have to do it like
    Exec= bash -c "sleep 5 && python -u /usr/share/screenlets/screenlets-pack-basic/Lipik/LipikScreenlet.py"

```


   so what should I do? run Exec= bash -c "sleep 5 && python -u /usr/share/screenlets/screenlets-pack-basic/Lipik/LipikScreenlet.py" in the Terminal?


Thanks
Bye

If you set a screenlet to autostart it places a .desktop file in **~/.config/autostart**
The tilde character (~) is short for /home/*[COLOR="DimGray"]username[/COLOR]*...eg /home/*[COLOR="dimgray"]Silentwave[/COLOR]*
The .config folder is hidden because of the preceding dot.

So open up the file browser and press ctrl+h to show hidden files.
Goto the **.config** folder and then the **autostart** folder.
Look for the appropriate screenlet.desktop file...eg the file for the lipik screenlet is called **LipikScreenlet.desktop**

Open gedit and drag and drop **your** screenlet.desktop file into gedit.

Then add **bash -c "sleep 5 &&** to the front of the exec line and a double quote to the end.

The example given was using the lipik screenlet.
The original .desktop file for the lipik screenlet would look like 
```
[Desktop Entry]
Name=LipikScreenlet
Encoding=UTF-8
Version=1.0
Type=Application
Exec= [COLOR="darkorchid"]python -u /usr/share/screenlets/screenlets-pack-basic/Lipik/LipikScreenlet.py[/COLOR]
X-GNOME-Autostart-enabled=true
```


The edited file would look like
```
[Desktop Entry]
Name=LipikScreenlet
Encoding=UTF-8
Version=1.0
Type=Application
Exec= [COLOR="Red"]bash -c "sleep 5 &&[/COLOR] [COLOR="darkorchid"]python -u /usr/share/screenlets/screenlets-pack-basic/Lipik/LipikScreenlet.py[/COLOR][COLOR="red"]"[/COLOR]
X-GNOME-Autostart-enabled=true
```

You need to edit your particular screenlet.desktop file in the same manner.
Don't change the original line, just add the **[COLOR="red"]bash -c "sleep 5 &&[/COLOR]** part
and the quotation mark to the end.Spaces are important.

---

### Post by Guido Tabbernuk on 2011-12-20
> **Silentwave said:**
> Ok, I read the bug, and in fact the solution is to delay screenlets on start with this:
I'm sorry if the bug report is not clear enough, but it says, that the fix for the bug has been committed and fixed version of Screenlets should be available in Dev PPA. So you just have to install latest Screenlets to fix this and you can skip modifying the autostart files. Although, delaying also helps to reduce the problem, if you don't want to install Dev version.

The fix is also documented here with the instructions how to install Screenlets from Development PPA: [http://askubuntu.com/questions/83411/screenlets-change-position-after-restart](http://askubuntu.com/questions/83411/screenlets-change-position-after-restart)

Development PPA is here: [https://launchpad.net/~screenlets-dev/+archive/ppa](https://launchpad.net/~screenlets-dev/+archive/ppa)

The fixes will probably move to normal Screenlets PPA in some weeks, when it's clear nothing else is broken in latest Development version.

---

### Post by Silentwave on 2011-12-20
> **stinkeye said:**
> If you set a screenlet to autostart it places a .desktop file in **~/.config/autostart**
The tilde character (~) is short for /home/*[COLOR=DimGray]username[/COLOR]*...eg /home/*[COLOR=dimgray]Silentwave[/COLOR]*
The .config folder is hidden because of the preceding dot.

So open up the file browser and press ctrl+h to show hidden files.
Goto the **.config** folder and then the **autostart** folder.
Look for the appropriate screenlet.desktop file...eg the file for the lipik screenlet is called **LipikScreenlet.desktop**

Open gedit and drag and drop **your** screenlet.desktop file into gedit.

Then add **bash -c "sleep 5 &&** to the front of the exec line and a double quote to the end.

The example given was using the lipik screenlet.
The original .desktop file for the lipik screenlet would look like 
```
[Desktop Entry]
Name=LipikScreenlet
Encoding=UTF-8
Version=1.0
Type=Application
Exec= [COLOR=darkorchid]python -u /usr/share/screenlets/screenlets-pack-basic/Lipik/LipikScreenlet.py[/COLOR]
X-GNOME-Autostart-enabled=true
```
The edited file would look like
```
[Desktop Entry]
Name=LipikScreenlet
Encoding=UTF-8
Version=1.0
Type=Application
Exec= [COLOR=Red]bash -c "sleep 5 &&[/COLOR] [COLOR=darkorchid]python -u /usr/share/screenlets/screenlets-pack-basic/Lipik/LipikScreenlet.py[/COLOR][COLOR=red]"[/COLOR]
X-GNOME-Autostart-enabled=true
```You need to edit your particular screenlet.desktop file in the same manner.
Don't change the original line, just add the **[COLOR=red]bash -c "sleep 5 &&[/COLOR]** part
and the quotation mark to the end.Spaces are important.
Perfect man, problem solved :)

---

### Post by Hellweek on 2011-12-20
> **thaelim said:**
> Suffice it to say I'm a Python veteran of 10 years and I can tell the difference between good and poor quality code. I have also tried screenlets for many months myself (and modified them for my own purposes). 

There is a reason there is a Conky thread in the Cafe with nearly 19,000 posts and over 4 million views, and no similarly popular screenlets thread.

It is a shame that Conkey is a pain in the butt to configure.  I never did get it working correctly.

---

### Post by stinkeye on 2011-12-20
> **Hellweek said:**
> It is a shame that Conkey is a pain in the butt to configure.  I never did get it working correctly.
Configuring conky enabled me to learn how to use linux.
Found out how to use curl, grep, sed, awk and how to write simple scripts.
Great way to learn under the bonnet stuff if your a tinkerer.

---

