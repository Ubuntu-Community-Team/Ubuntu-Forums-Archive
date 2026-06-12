---
title: "most damage a troll can make without root access"
date: 2011-10-30
forum: General Help
---

### Post by van_Zeller on 2011-10-30
Hi all,

I'm working in a hostel that has a computer for the guests to use. this computer (a simple nettop) was struggling with all the stuff it had, plus Vista, so I installed ubuntu 11.10. It's nice, clean, legal and fast. So far, so good.

What worries me is that it's a pretty standard ubuntu installation, because I really don't know how to set up an internet kiosk. You can, for instance, open a terminal.

So, my question is: what is the worst a possible linux-knowing troll could do, using the terminal, without having access to the root password?

---

### Post by enkay009 on 2011-10-30
I'm really looking forward to what some of the experts have to say about this.

However as someone who (occasionally) likes mess to around with public PCs (basically troll), I'd try to fork a bunch of processes to eat up CPU and memory, and maybe fill up the hard drive (home directory, temp, whatever I have access to).

---

### Post by haqking on 2011-10-30
> **van_Zeller said:**
> Hi all,

I'm working in a hostel that has a computer for the guests to use. this computer (a simple nettop) was struggling with all the stuff it had, plus Vista, so I installed ubuntu 11.10. It's nice, clean, legal and fast. So far, so good.

What worries me is that it's a pretty standard ubuntu installation, because I really don't know how to set up an internet kiosk. You can, for instance, open a terminal.

So, my question is: what is the worst a possible linux-knowing troll could do, using the terminal, without having access to the root password?

Physical access is root access.

They can drop to a recovery console and root shell prompt

They could potentially boot to a Live CD, or use a USB

Physical is root

---

### Post by Gremlinzzz on 2011-10-30
> **van_Zeller said:**
> Hi all,

I'm working in a hostel that has a computer for the guests to use. this computer (a simple nettop) was struggling with all the stuff it had, plus Vista, so I installed ubuntu 11.10. It's nice, clean, legal and fast. So far, so good.

What worries me is that it's a pretty standard ubuntu installation, because I really don't know how to set up an internet kiosk. You can, for instance, open a terminal.

So, my question is: what is the worst a possible linux-knowing troll could do, using the terminal, without having access to the root password?

change the password:popcorn: or install a windows look alike theme

---

### Post by van_Zeller on 2011-10-30
> **Gremlinzzz said:**
> change the password:popcorn:

You can change the password without knowing the previous password??

---

### Post by Gremlinzzz on 2011-10-30
> **van_Zeller said:**
> You can change the password without knowing the previous password??

yes i can:popcorn:

---

### Post by lykwydchykyn on 2011-10-30
Well, they could pretty much trash the desktop, fill the browser with nasty shortcuts, drop scripts in there to do all kinds of malicious things.

But rather than discuss that, why don't we discuss how to lock this thing down properly?

I've set up a few internet kiosks in my day, usually I just override the kiosk user's .xinitrc file to only launch a simple window manager, rsync a fresh copy of the home directory, then launch a browser full-screen in an endless loop (so that when the browser is closed it just relaunches).

Basically, my .xinitrc might look something like this:
```

xset s off
xset -dpms

matchbox-window-manager &

while true; do
  rsync -qr --delete /usr/local/kiosk/ /home/kiosk/
  chromium-browser --app=http://example.com
done

```

This, of course, assumes that you have matchbox-window-manager installed, and that you have a clean copy of kiosk's home directory under /usr/local (you can put it anywhere that isn't writeable by the kiosk user).

Let me know if this sounds useful, I can offer more suggestions.  Been doing this kind of thing for years.

---

### Post by Nixarter on 2011-10-30
> **van_Zeller said:**
> You can change the password without knowing the previous password??
Yes. That is one of the implications of the method haqking mentioned.

But basically, they can do anything they want.  I'm sure there are ways to make it less obviously open, though.

All that same stuff can be done in windows as well.

---

### Post by F.G. on 2011-10-30
so, i guess that there isn;t really anything you can do about the live cd/usb issue (except using a secure booted device).  the ubuntu having no root password is something that can apparently be changed, which might be advisable. also you could look at using open suse or fedora, or another distro, which uses root password.

i seem to remember that windows has a program called deepfreeze, which prevents users affecting any changes to it.

also i think a fork-bomb still works, to make to make Ubuntu freeze up. eg:
<snip>

---

### Post by sammiev on 2011-10-30
> **F.G. said:**
> so, i guess that there isn;t really anything you can do about the live cd/usb issue (except using a secure booted device).  the ubuntu having no root password is something that can apparently be changed, which might be advisable. also you could look at using open suse or fedora, or another distro, which uses root password.

i seem to remember that windows has a program called deepfreeze, which prevents users affecting any changes to it.

also i think a fork-bomb still works, to make to make Ubuntu freeze up. eg:
<snip>

You can only keep the honest person out.

---

### Post by F.G. on 2011-10-30
> **sammiev said:**
> You can only keep the honest person out.

this seems to often be the case with many different types of rules and laws.

---

### Post by lykwydchykyn on 2011-10-30
If you: 
 - disable booting from anything but the main HDD in BIOS
 - Lock down the BIOS with a password
 - Lock down the recovery entries in GRUB with a password
 - padlock the chassis

Then you'll have effectively taken care of the LiveCD/USB issue for the casual troll.  There aren't many people out there determined enough to troll to cut through a padlock and yank out the MB battery.

Alternately, lock the CPU in a ventilated cabinet.  No media, no liveboot.

---

### Post by dcstar on 2011-10-31
> **van_Zeller said:**
> Hi all,

I'm working in a hostel that has a computer for the guests to use. this computer (a simple nettop) was struggling with all the stuff it had, plus Vista, so I installed ubuntu 11.10. It's nice, clean, legal and fast. So far, so good.

What worries me is that it's a pretty standard ubuntu installation, because I really don't know how to set up an internet kiosk. You can, for instance, open a terminal.

So, my question is: what is the worst a possible linux-knowing troll could do, using the terminal, without having access to the root password?

You could always remove the hard drive and just leave a Ubuntu Live CD locked in the CD drive and boot off that - or a Live USB device inside the PC with no persistence.

Fresh system with each boot.

---

### Post by gsmanners on 2011-10-31
> **lykwydchykyn said:**
> Alternately, lock the CPU in a ventilated cabinet.  No media, no liveboot.

I like this idea. Nice. :D

Just make sure you have it on a UPS, first.

---

### Post by van_Zeller on 2011-10-31
The bios is locked already, so it's not possible (afaik) to boot from a usb drive without this password.

Also, I will disable the recovery mode as soon as I can get to it.

> **dcstar said:**
> You could always remove the hard drive and just leave a Ubuntu Live CD locked in the CD drive and boot off that - or a Live USB device inside the PC with no persistence.

Fresh system with each boot.

I was thinking about this as I fell asleep yesterday: I could set up a "master" copy of the home folder somewhere where the user has no write permissions. On each reboot I could replace whatever was in the home folder with this "clean" version (using a script +  cron)

What do you thing of this solution?

---

### Post by van_Zeller on 2011-10-31
> **lykwydchykyn said:**
> Well, they could pretty much trash the desktop, fill the browser with nasty shortcuts, drop scripts in there to do all kinds of malicious things.

But rather than discuss that, why don't we discuss how to lock this thing down properly?

I've set up a few internet kiosks in my day, usually I just override the kiosk user's .xinitrc file to only launch a simple window manager, rsync a fresh copy of the home directory, then launch a browser full-screen in an endless loop (so that when the browser is closed it just relaunches).

Basically, my .xinitrc might look something like this:
```

xset s off
xset -dpms

matchbox-window-manager &

while true; do
  rsync -qr --delete /usr/local/kiosk/ /home/kiosk/
  chromium-browser --app=http://example.com
done

```

This, of course, assumes that you have matchbox-window-manager installed, and that you have a clean copy of kiosk's home directory under /usr/local (you can put it anywhere that isn't writeable by the kiosk user).

Let me know if this sounds useful, I can offer more suggestions.  Been doing this kind of thing for years.

Just read this properly. Sounds like a great idea, except for the browser loop. I don't want to restrict my guests *that* much, they sometimes need to edit a file or something (think boarding passes, or long emails, shared expeses on excel etc). Also, the night shift guys uses the machine to study, he may need libreoffice as well.

---

### Post by lykwydchykyn on 2011-10-31
> **van_Zeller said:**
> Just read this properly. Sounds like a great idea, except for the browser loop. I don't want to restrict my guests *that* much, they sometimes need to edit a file or something (think boarding passes, or long emails, shared expeses on excel etc). Also, the night shift guys uses the machine to study, he may need libreoffice as well.

That's just an example.  You can launch any desktop shell you want to launch there, the key is the rsync which does what you were just describing -- copies a fresh copy of the home directory from a read-only location.

If you want to restrict what apps can be used, sound like a good task for apparmor.

---

### Post by Lars Noodén on 2011-10-31
> **lykwydchykyn said:**
> That's just an example.  You can launch any desktop shell you want to launch there, the key is the rsync which does what you were just describing -- copies a fresh copy of the home directory from a read-only location.

+1

Be sure to use the option --delete with rsync to remove extraneous files from the home directory.

---

### Post by Gremlinzzz on 2011-10-31
How vicious is this Troll cause he could take a hammer and:popcorn:

---

### Post by Elfy on 2011-10-31
forkbombs removed - see forum announcement.

ATTENTION ALL USERS: Malicious Commands

... UbuntuForums has a strict zero-tolerance policy when it comes to posting dangerous commands ...

[http://ubuntuforums.org/announcement.php?f=150](http://ubuntuforums.org/announcement.php?f=150)

---

### Post by F.G. on 2011-10-31
hey, 
so i'm sorry if anyone mistook the post i made earlier regarding a certain command. it was in no way intended maliciously and i hope that the context was clear that it was not intended for people to execute. and i do respect the forum rules. 
I do however also believe that forewarned is forearmed.

@forestpixie i can't seem to access that link, don't know why (if my account is under review then i probably shouldn't be able to make this post)

---

### Post by Elfy on 2011-10-31
> **F.G. said:**
> hey, 
so i'm sorry if anyone mistook the post i made earlier regarding a certain command. it was in no way intended maliciously and i hope that the context was clear that it was not intended for people to execute. and i do respect the forum rules. 
I do however also believe that forewarned is forearmed.

@forestpixie i can't seem to access that link, don't know why (if my account is under review then i probably shouldn't be able to make this post)
No reason why you shouldn't be able to - can you see the Blue Banner with the 'youtube' announcement at the top of forums pages? - The malicious commnds post is the third post in announcements.

I realise that the intent was not malicious - but someone wandering around could find it and then wish they'd not.

If you can't see the announcement perhaps you could let me know and I'll get someone to look into it - at one point it went walkabout and people couldn't see it.

---

### Post by gsmanners on 2011-10-31
> **forestpiskie said:**
> forkbombs removed - see forum announcement.

ATTENTION ALL USERS: Malicious Commands

... UbuntuForums has a strict zero-tolerance policy when it comes to posting dangerous commands ...

[http://ubuntuforums.org/announcement.php?f=150](http://ubuntuforums.org/announcement.php?f=150)

I think that got moved to: [http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

---

### Post by Elfy on 2011-10-31
> **gsmanners said:**
> I think that got moved to: [http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

Oh - thanks :)

I can see it in both places ... 

That might explain that then.

---

