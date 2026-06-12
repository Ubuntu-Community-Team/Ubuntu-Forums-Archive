---
title: "How to change default applications registered with Ubuntu's default messaging menu?"
date: 2012-08-17
forum: General Help
---

### Post by sunny_sigara on 2012-08-17
As default, following applications are registered with messaging menu.
[HTML]
    Chat-> Empathy
    Mail-> Thunderbird[/HTML]

What I want to do is:
[HTML]
    Chat-> Pidgin
    Mail-> Evolution[/HTML]

[IMG]http://i.imgur.com/hGogw.png[/IMG]


If you install evolution (& evolution-indicator) or pidgin it will appear as a seperate menu inside messaging menu.It doesn't register with default menu , even if you uninstall the default applications.

The only way to remove them(default chat & mail menu) is to blacklist them.

**[SIZE="2"]A trick that has worked before[/SIZE]**
--------------------------------------------
After fresh install, If you click messaging menu,there are option like `setup chat` , `set up mail`..etc. 

***Now before doing anything, if you remove thunderbird & install evolution,then after restart when you first click on `setup mail` it automatically starts evolution setup!! It doesn't create a separate menu named 'evolution`.***

Same thing with pidgin. BUT these only works after fresh install.

I think when you first click `**setup mail**` or `**chat**` it somehow register the default mail or chat client with `**Mail**` & `**Chat**` menu respectively. What I want is to undo these change.

So How do I reset messaging menu to factory default?

---

### Post by sunny_sigara on 2012-08-20
OK Found it! Messaging menu actually uses alphabetical order.So chat comes before evolution or gwibber. So the order is for various applications which use messaging menu is like this:

```
chat->Emapthy->Evolution->Gwibber->Liferea->Ubuntu One->X-chat
```

So when using pidgin, the file-name (under /usr/share/indicators/messages/applications) has to be changed to "**chat**" from "**pidgin**".

But the file content remains the same which is 
```
/usr/share/application/pidgin.desktop
```.

Also the name section of the desktop file (in above case pidgin.desktop)has to be changed to "**chat**" from "**pidgin**".

Finally one needs to recompile messaging menu replacing "**emapthy.desktop**" with "**pidgin.desktop**" inside ***default-application.c*** 
file located under ***/src*** directory of the source package( indicator-messages-$version/src).

[IMG]http://i.imgur.com/6pkpL.png[/IMG]

Same with Evolution/Thunderbird.

Thats ALL!
DONE!

---

