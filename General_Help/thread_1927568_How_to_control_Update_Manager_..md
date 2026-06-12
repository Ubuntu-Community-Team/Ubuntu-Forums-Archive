---
title: "How to control Update Manager ."
date: 2012-02-18
forum: General Help
---

### Post by susja on 2012-02-18
Hello,
I have an issue with my Update Manager. I recently installed Ubuntu 11.10. Almost every day Update Manager finds a new updates and offer me to install it. But I absolutely don't have control over it. I mean I can't open Update Manager, I can't see which updates it wants to install and etc. I can't even open Update Manager. The only thing that I could do is to allow it to install updates. Well this is not acceptable. Could someone tell me please how could I fix it? Maybe I could just uninstall and then install back Update Manager or etc?
Appreciate any help.
susja

---

### Post by mcduck on 2012-02-18
What happens if you try opening it from the Dash menu (or search)? And what happens if you try running "update-manager" from a terminal?

---

### Post by cortman on 2012-02-18
Not sure what you mean by "no control".

I opened Update Manager on my Lubuntu 11.10 just now, and I see 

a) a list of the names of every package it plans to update
b) Click the liittle "down arrow" by "Description of update" and you get a list of the things it will change about the packages, plus an excellent description of the purpose of the package and the update itself, on the "Description" tab.

Then you can check/uncheck the packages you want to install or not.

Don't see how much more control you can get. ???

---

### Post by ajgreeny on 2012-02-18
> **cortman said:**
> Not sure what you mean by "no control".

I opened Update Manager on my Lubuntu 11.10 just now, and I see 

a) a list of the names of every package it plans to update
b) Click the liittle "down arrow" by "Description of update" and you get a list of the things it will change about the packages, plus an excellent description of the purpose of the package and the update itself, on the "Description" tab.

Then you can check/uncheck the packages you want to install or not.

Don't see how much more control you can get. ???
I think you will find that it is easier to use that way in Lubuntu than it is in Ubuntu.  I also seem to remember reading that the update manager in Ubuntu 11.10 updates everything automatically, without the need for a password.  I'm not using ubuntu 11.10, so I may be wrong about that.

Can I also ask if update manager still opens a window in the background in minimised state, as it does by default in versions from 10.04.  I found this an enormous nuisance, as it would be open, but minimised sometimes when I was doing other things needing to use apt, and therefore everything ground to a halt.  I quickly changed that back to the old default of just a notification that updates are available, rather than the update manager opening all by itself.  Can that behaviour even be changed in Unity; so many things can't be configured to one's liking any more.

---

### Post by cortman on 2012-02-18
H'm, just opened Update Manager on my Ubuntu 11.10 installation and it's identical. I have all the same options (including deselect packages) as Lubuntu...

---

### Post by ajgreeny on 2012-02-18
> **cortman said:**
> H'm, just opened Update Manager on my Ubuntu 11.10 installation and it's identical. I have all the same options (including deselect packages) as Lubuntu...
Fair enough!  As I said, I don't run Ubuntu 11.10, so wasn't sure.

What about my question of update-manager opening minimised in the background rather than simply notifying that updates are available; does that still happen?

---

### Post by mcduck on 2012-02-18
> **ajgreeny said:**
> Fair enough!  As I said, I don't run Ubuntu 11.10, so wasn't sure.

What about my question of update-manager opening minimised in the background rather than simply notifying that updates are available; does that still happen?

It's configurable, the default behaviour is to open the Update Manager window automatically, max once per every seven days (apart from important security updates, which cause the Update Manager to pop up immediately).

As far as I know it has never been purposefully opened *minimized*, although depending on the window manager you use and it's settings, and what you do on the computer at the time, that could probably happen. The designed way is that it's supposed to pop up on top of whatever you are doing at the time.

(and like I said, it's configurable, I personally prefer just a  notification icon instead of the window popping up.)

---

### Post by ajgreeny on 2012-02-18
> **mcduck said:**
> It's configurable, the default behaviour is to open the Update Manager window automatically, max once per every seven days (apart from important security updates, which cause the Update Manager to pop up immediately).

As far as I know it has never been purposefully opened *minimized*, although depending on the window manager you use and it's settings, and what you do on the computer at the time, that could probably happen. The designed way is that it's supposed to pop up on top of whatever you are doing at the time.

(and like I said, it's configurable, I personally prefer just a  notification icon instead of the window popping up.)
I am pretty certain that until 10.04, or maybe 9.10, the default was just to display a notification then it changed to the update-manager opening.  Perhaps I use the wrong description when I say that update-manager opens minimised, but the default is now for it to open, thereby stopping any apt-get activities that you may be doing, which is a real nuisance, in my opinion.

---

### Post by cortman on 2012-02-18
Update manager does startup automatically in 11.10 and 11.04, but I don't think it starts downloading until you push the big red button, so to speak. That's those versions, anyhow.

---

### Post by Paqman on 2012-02-18
> **ajgreeny said:**
> 
Can I also ask if update manager still opens a window in the background in minimised state, as it does by default in versions from 10.04

No, they changed that one pretty promptly because as you say, it was annoying. You now get a notification in your panel if there are updates available, which you can use to launch Update Manager.

---

### Post by mcduck on 2012-02-19
> **ajgreeny said:**
> I am pretty certain that until 10.04, or maybe 9.10, the default was just to display a notification then it changed to the update-manager opening.  Perhaps I use the wrong description when I say that update-manager opens minimised, but the default is now for it to open, thereby stopping any apt-get activities that you may be doing, which is a real nuisance, in my opinion.

Yes, that's true, the default used to be just a notification, but it was changed to popping up the window, just to make sure that all users actually notice that there are updates available.

If you want to, you can get back to the old behaviour, although sadly there's no option for it in the menus (you need to use dconf/Gsettings). So what you need to do is install [dconf-tools]("apt:dconf-tools") and then use dconf-editor to browse to *com.ubuntu.update-notifier*, and set *auto-launch* to *false*.

...or just pop open a terminal and run the following command:
```
gsettings set com.ubuntu.update-notifier auto-launch false
```

(If it's not working for you, and you don't see the icon even though you know there are updates available, make sure *com.canonical.Unity.Panel systray-whitelist* has *'Update-notifier'* included. (It should be by default in 11.10, but if I rember right it wasn't there by default in 11.04...)

---

### Post by susja on 2012-02-19
> **mcduck said:**
> What happens if you try opening it from the Dash menu (or search)? And what happens if you try running "update-manager" from a terminal?
Either I run from Dash menu or from command line nothing happened i.e. Update Manager doesn't open.

---

### Post by susja on 2012-02-19
> **cortman said:**
> Not sure what you mean by "no control".

I opened Update Manager on my Lubuntu 11.10 just now, and I see 

a) a list of the names of every package it plans to update
b) Click the liittle "down arrow" by "Description of update" and you get a list of the things it will change about the packages, plus an excellent description of the purpose of the package and the update itself, on the "Description" tab.

Then you can check/uncheck the packages you want to install or not.

Don't see how much more control you can get. ???
I understand that and it's exactly  what I meant by control. The only difference is that in my case I failed to open Update Manager :)

---

### Post by susja on 2012-02-19
> **cortman said:**
> Update manager does startup automatically in 11.10 and 11.04, but I don't think it starts downloading until you push the big red button, so to speak. That's those versions, anyhow.
-cortman,
It does not download until I push the button. It will download all packages when I do push the button. The issue is that I can't open it to check what updates it's going to install.

---

### Post by susja on 2012-02-19
> **mcduck said:**
> Yes, that's true, the default used to be just a notification, but it was changed to popping up the window, just to make sure that all users actually notice that there are updates available.

If you want to, you can get back to the old behaviour, although sadly there's no option for it in the menus (you need to use dconf/Gsettings). So what you need to do is install [dconf-tools]("apt:dconf-tools") and then use dconf-editor to browse to *com.ubuntu.update-notifier*, and set *auto-launch* to *false*.

...or just pop open a terminal and run the following command:
```
gsettings set com.ubuntu.update-notifier auto-launch false
```

(If it's not working for you, and you don't see the icon even though you know there are updates available, make sure *com.canonical.Unity.Panel systray-whitelist* has *'Update-notifier'* included. (It should be by default in 11.10, but if I rember right it wasn't there by default in 11.04...)
hi mcduck,
I changed auto-launch to false in update-notifier using dconf-editor.
What should I do now? Just click on 'Install all available Updates'?
I don't see other option to expect to see a list of updates.

---

### Post by susja on 2012-02-19
Well ... I have to correct myself. I was not able to open Update Manager and check the list of updates. Eventually I just clicked on 'Install all available updates' and after it updated my system I could now open Update Manager and get to settings and etc. Well that's still weird since I want to open it before I updated system  but not after the fact. I still want to know what packages I'm going to apply.

---

### Post by cortman on 2012-02-19
Real basic question: there isn't any pull-down menu or something you're missing, is there? I had to click "Description" to see more details on the packages.

---

### Post by susja on 2012-02-21
Hey folks.
Thanks for all your responds. After changes I made based on your replies now I've got notification and a list of updates.

I am all set now.
You all are very helpful.

---

### Post by cortman on 2012-02-21
Great! Mark this as [SOLVED] if you would, using the thread tools in the upper right.

---

