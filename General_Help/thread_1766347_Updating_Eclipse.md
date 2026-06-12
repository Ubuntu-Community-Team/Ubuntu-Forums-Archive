---
title: "Updating Eclipse"
date: 2011-05-24
forum: General Help
---

### Post by musex on 2011-05-24
Hi everyone :P
I use eclipse 3.5.2 for developing web applications (servlets,JSP) and Java programs. The problem is that I don't know how to update it, I mean it's not updated automatically through the update manager, so I guess I need to add something in the repositories. Anyway inside eclipse, in the help menu, there's the button "check for updates", but after it searches for new versions, it says "there's nothing to update".Is there a way to update it through the update manager? And how can I do it? 
thanks :)

---

### Post by musex on 2011-05-24
Anyone? :confused:

---

### Post by dragonfly41 on 2011-05-24
I've launched my Eclipse Galileo to test this ..

After selecting Help > Check for Updates

I see a message .. Contacting Software Sites

contacting [http://download.eclipse.org/releases/galileo/](http://download.eclipse.org/releases/galileo/)

[http://download.eclipse.org/releases/galileo/content.jar](http://download.eclipse.org/releases/galileo/content.jar)

and then a popup message ..

Information
"There is nothing to update"

...

Perhaps there are no updates?

---

### Post by musex on 2011-05-24
:)Actually there is a new version, Helios 3.6.2 ...

---

### Post by Azdour on 2011-05-25
Hi,

I'm not sure you can update from 3.5 to 3.6 and the version in Synaptic Package Manager (on Ubuntu 10.04) is still 3.5

I use Eclipse for my development work, I have never installed it from Synaptic I just download Eclipse from their website. This is how I upgraded from 3.5 to 3.6.

---

### Post by musex on 2011-05-25
So I guess I'll just have to download the new version. I was hoping for a better solution, thanks anyway :)

---

### Post by Azdour on 2011-05-25
Hi,

You've made me curious about how to upgrade from 3.5 to 3.6 :)  So I did some googling and found this:

[http://wiki.eclipse.org/FAQ_How_do_I_upgrade_Eclipse%3F](http://wiki.eclipse.org/FAQ_How_do_I_upgrade_Eclipse%3F)

---

### Post by musex on 2011-05-25
> **Azdour said:**
> Hi,

You've made me curious about how to upgrade from 3.5 to 3.6 :)  So I did some googling and found this:

[http://wiki.eclipse.org/FAQ_How_do_I_upgrade_Eclipse%3F](http://wiki.eclipse.org/FAQ_How_do_I_upgrade_Eclipse%3F)

Ok I followed the guide you linked,and in fact the program finds some updates available,but it doesn't let me update 'cause it says :
```
The software items you selected may not be valid with your current installation.Do you want to open the wizard anyway to review the selections?
```
and as I click yes it opens me this window:
[ATTACH]193124[/ATTACH]
Any suggestions?:confused:

---

### Post by Azdour on 2011-05-25
Hi,

I'm only guessing, but it looks like you have one or more plugins that are limited to 3.5 (e.g. in their feature.xml they specify a specific eclipse version) and not 3.6 hence the conflict:

[http://www.eclipse.org/forums/index.php/mv/msg/205285/662440/](http://www.eclipse.org/forums/index.php/mv/msg/205285/662440/)

There maybe a solution but for me its too messy ([http://plosquare.blogspot.com/2011/04/fix-for-cannot-complete-install-because.html](http://plosquare.blogspot.com/2011/04/fix-for-cannot-complete-install-because.html)). I'd rather install 3.6 from eclipse and then re-install any additional plugins that I have been using in 3.5.

I'm sorry that I cannot help you any further with this.

---

### Post by musex on 2011-05-25
Ok I guess that's what I'm gonna do...
thanks :)

---

