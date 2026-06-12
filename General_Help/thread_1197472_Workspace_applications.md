---
title: "Workspace applications"
date: 2009-06-26
forum: General Help
---

### Post by superdx on 2009-06-26
Hi there,

Just installed ubuntu 9.04, I'm liking it OK, and I really like the Workspaces feature. I created difference workspaces for my applications and was happily switching back and forth.

Fast forward to next day, I boot up Ubuntu and *gasp* all my applications are now in the first workspace. It took me 30 minutes just to move everything back the way it was. Confirming my fears, I rebooted again and all the stuff ended back in workspace 1. 

Isn't there any way to remember which space the application should belong to?

And if I close the application and start it again, shouldn't it open in the same workspace again, and not in workspace 1?

Any help would be appreciated!

---

### Post by CatKiller on 2009-06-26
> **superdx said:**
> And if I close the application and start it again, shouldn't it open in the same workspace again, and not in workspace 1?

Applications open on the workspace that is selected when the window is created. I don't know if there's a simple way to have applications open on the same workspace they last appeared.

I'd imagine that you could get particular windows to open on a particular workspace with either the Compiz Place Windows plugin or with DevilsPie, though.

---

### Post by superdx on 2009-06-27
I don't really get this part - if I have 8 workspaces open, each filled with applications, I reboot, they all go back to workspace 1?

Sounds like this feature isn't exactly thought through

---

### Post by CatKiller on 2009-06-27
> **superdx said:**
> I don't really get this part - if I have 8 workspaces open, each filled with applications, I reboot, they all go back to workspace 1?

No. If you close all your applications and re-open them, they re-open where you've opened them. There's no real reason why that should be Workspace 1.

As I said, Compiz (if that's your window manager) or DevilsPie (if it isn't) are both capable of doing what you want. Or there are plenty of other window managers available. Or you can feel free to code the behaviour you want and patch Metacity.

---

### Post by superdx on 2009-06-27
I'm don't have any programming experience, much less fiddling with application source code

Guess I'll just wait another year or two before I try Linux again, thanks for your help

---

### Post by CatKiller on 2009-06-27
> **superdx said:**
> Guess I'll just wait another year or two before I try Linux again

Why? The tools to do what you want are already there. You haven't said which window manager you're using, so no one can tell you the best way to do what you want to do.

Why would you change operating systems based on such a small feature when, AFAIK, Windows doesn't have workplaces at all?

---

### Post by superdx on 2009-06-27
I'm using Gnome? I mentioned I was using Ubuntu. Unless you're asking about something else. I tried the Compiz settings and it's asking me for things like Window class and X and Y coordinates. I have no idea what to even put in. I tried a few settings and the windows smashed themselves into the top right of my screen and I couldn't pull them out again.

It's not really a small feature, I use the same functionality in OSX and it took me 20s to figure out.

---

### Post by CatKiller on 2009-06-27
> **superdx said:**
> I'm using Gnome? I mentioned I was using Ubuntu. Unless you're asking about something else.

If you're not using any Desktop Effects then you're probably using Metacity (since that's the default window manager for Gnome). If you are using Desktop Effects then you're using Compiz (the other window manager that comes with a default install of Ubuntu). Having not said if you were using Desktop Effects, it's impossible to distinguish between the two from the fact that you're using Ubuntu 9.04. Since you've said that using CCSM had an effect, I'll assume you're using Compiz.

> 
I tried the Compiz settings and it's asking me for things like Window class and X and Y coordinates. I have no idea what to even put in. I tried a few settings and the windows smashed themselves into the top right of my screen and I couldn't pull them out again.

I found some documentation for the Place Windows plugin [here]("http://wiki.compiz-fusion.org/Plugins/Place"). The gist of it seems to be that you specify which workspace you want to use as a co-ordinate starting at 1 for the layout that you're using in the "fixed viewport" section. I have no idea whether your 8 workspaces are laid out as a line of workspaces, or two columns of 4, or what. But I just tried it with Thunderbird, and it opened on the second workspace along as I'd specified. You can also specify a particular window position for the application using the "fixed position" section if that's what you want too.

> It's not really a small feature, I use the same functionality in OSX and it took me 20s to figure out.

Fair enough. It's not something that I've been particularly interested in, so I've not been looking out for it especially. I've not yet come across a setting to remember all the window positions automatically but, as I said, I've not been looking.

---

### Post by gldearman on 2009-06-27
Hi, superdx,

Welcome to Ubuntu!  Thanks for trying it.  Sorry you are having a problem.

I, for one, really like the way the applications relate to the workspaces in Gnome.  But, clearly, you want a different behavior (one that would drive me nuts!).

Devil's Pie is in the repositories, and is intended for exactly this purpose.  You may find it easier to configure and use than the Compiz Fusion plugin that is confusing you.

There are other alternatives.  I am pretty sure that relating an application with a particular workspace is much easier in the KDE desktop than in Gnome.  I don't use KDE, but a friend of mine runs KDE under the PCLOS distro, and he has one workspace for media, one for internet, one for office, etc.  Whenever he opens Open Office, it opens in the "Office" workspace.  So, you might want to give Kubuntu a try instead.  Remember, you don't have to uninstall Ubuntu to try Kubuntu -- you can have them both installed at once (since they are just different "faces" on the same OS).

Another option might be to not shut down.  Really.  Just hibernate Ubuntu when you are down with it.  A hibernating computer should use no more power than a shut down computer, and *should* maintain all of your windows wherever you want them.  Again, I don't hibernate, so I don't know, but that's the way it's supposed to work.  Of course, eventually you are going to *have* to restart.

---

