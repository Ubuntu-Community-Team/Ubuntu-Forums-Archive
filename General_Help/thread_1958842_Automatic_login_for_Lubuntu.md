---
title: "Automatic login for Lubuntu?"
date: 2012-04-15
forum: General Help
---

### Post by Roasted on 2012-04-15
Tinkering around with 12.04 here and I'd like to enable automatic login. Best I see, GUI based, is "remove need for password to log in" but it's not actual automatic login. I also edited a file based on [these instructions]("http://www.itworld.com/software/243325/enable-automatic-login-lubuntu-1110") but no dice... I want automatic login so that way my VNC service kicks on so I can remove in on my desktop (unless anybody knows a way to allow VNC to kick on before logging in??)

Anybody know how to do that?

Secondly, what's up with Lubuntu's RAM consumption? My 12.04 Unity systems eat about 250 MB of RAM average on fresh boot, some of them even a little less. My Lubuntu 12.04 system is using 235 MB on fresh boot. No big deal, it works great, I'm just kind of surprised it took *that* much. Debian LXDE was less than half that... unless Lubuntu is just caching a bunch of stuff Debian isn't??

---

### Post by Rodney9 on 2012-04-15
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LightDM_in_Lubuntu_12.04](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LightDM_in_Lubuntu_12.04)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by MG&amp;TL on 2012-04-15
It shouldn't be using that much. Mine uses about 150 Mb on boot, decreasing to 125 thereafter. What's the biggest hog in your RAM meter? Some programs are a little buggy for some people, such as lxpanel.

---

### Post by Roasted on 2012-04-15
I'm a little disappointed in Lubuntu's lack of preinstalled remote desktop/VNC software. In Ubuntu, we have "Desktop Sharing" so set up our preferences for a user to remote in to our system.

What is the name of "Desktop Sharing" so I can install it on Lubuntu?

EDIT - It seems as if it is "vino". However, I installed vino, but I don't see it in the menu. A user in IRC was helpful enough to tell me I need to run "vino-preferences" in terminal. Uh, why? Why did this not create a menu option?

Lubuntu and I are not off to a good start. Already Ubuntu + LXDE is looking a little more logical.

---

### Post by MG&amp;TL on 2012-04-15
> **Roasted said:**
> I'm a little disappointed in Lubuntu's lack of preinstalled remote desktop/VNC software. In Ubuntu, we have "Desktop Sharing" so set up our preferences for a user to remote in to our system.

What is the name of "Desktop Sharing" so I can install it on Lubuntu?

EDIT - It seems as if it is "vino". However, I installed vino, but I don't see it in the menu. A user in IRC was helpful enough to tell me I need to run "vino-preferences" in terminal. Uh, why? Why did this not create a menu option?

Lubuntu and I are not off to a good start. Already Ubuntu + LXDE is looking a little more logical.

We're trying to keep it lightweight-some older computers cannot cope with an application such as vino.

It's not Lubuntu's fault the package maintainer did not provide a desktop file to provide a menuentry. :)

Lubuntu puts a layer of extra polish on your proposed combination. All Ubuntu+LXDE is going to do is the same problems without the extra polish.

---

### Post by Roasted on 2012-04-15
> **MG&TL said:**
> We're trying to keep it lightweight-some older computers cannot cope with an application such as vino.

It's not Lubuntu's fault the package maintainer did not provide a desktop file to provide a menuentry. :)

Lubuntu puts a layer of extra polish on your proposed combination. All Ubuntu+LXDE is going to do is the same problems without the extra polish.

I understand, however perhaps my directive of distro choice is a bit flawed in this instance. I was looking for a lightweight distro to remove as much GUI overhead as possible when I VNC into the box, despite the fact this box is a quad core with 4GB of RAM.

I'm eyeing up a straight install of Ubuntu and call it a day.

---

### Post by MG&amp;TL on 2012-04-15
Fair enough-with your box, the percentage overhead may be very little anyway.

Thanks for trying Lubuntu, hope Ubuntu serves you well. :)

---

### Post by Roasted on 2012-04-15
> **MG&TL said:**
> Fair enough-with your box, the percentage overhead may be very little anyway.

Thanks for trying Lubuntu, hope Ubuntu serves you well. :)

"Trying" Lubuntu? I may have been testing the waters with Lubuntu as my secondary "file/backup/video surveillance/torrent" server, but Lubuntu is what I run on my netbook exclusively. ;) But of course, what I use my netbook for and what I use this other box for are two different things, hence the point behind me making this thread as I ran into some snags.

It's all good, though. You were right, I don't think I really gained anything in terms of VNC speed. Unity seems quite responsive.

---

