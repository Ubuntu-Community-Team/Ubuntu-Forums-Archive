---
title: "I accidentally the whole computer"
date: 2010-06-07
forum: General Help
---

### Post by Cant on 2010-06-07
Before you read this I want you to know that while I usually know my way around computers I can still be a complete retard at times.

I was trying to uninstall Pidgin messenger in the Synaptic Package manager. I did a search for "Pidgin" and found it. I marked it for complete removal and Synaptic showed me a list of stuff that would be uninstalled with it. Me, being the idiot that I was, blindly clicked "ok" and stood back while it uninstalled Pidgin. But then I read "prepairing to remove brasero" and "prepairing to remove compiz", so in my panic I forced-quit Synaptic and rebooted. Now I can only log in to a terminal and don't know what to do. Someone please help.

---

### Post by boonenoob on 2010-06-07
ouch! it looks like you'll have to reinstall whichever Distro (OS) you're using.

---

### Post by wilee-nilee on 2010-06-07
> **Cant said:**
> Before you read this I want you to know that while I usually know my way around computers I can still be a complete retard at times.

I was trying to uninstall Pidgin messenger in the Synaptic Package manager. I did a search for "Pidgin" and found it. I marked it for complete removal and Synaptic showed me a list of stuff that would be uninstalled with it. Me, being the idiot that I was, blindly clicked "ok" and stood back while it uninstalled Pidgin. But then I read "prepairing to remove brasero" and "prepairing to remove compiz", so in my panic I forced-quit Synaptic and rebooted. Now I can only log in to a terminal and don't know what to do. Someone please help.

If you haven't shut down and you can open synaptic look in history it will tell what has been installed and removed.

---

### Post by wilee-nilee on 2010-06-07
> **boonenoob said:**
> ouch! it looks like you'll have to reinstall whichever Distro (OS) you're using.

I would be careful about saying this, it is a whole os that could have irreplaceable stuff on it. Does this make sense to you? No offers of recovery and just replace is not very helpful.

---

### Post by helliewm on 2010-06-07
Sounds like you have removed the Ubuntu-desktop. Plug a wired internet connection.

At the Terminal sudo apt-get install ubuntu-desktop.

then reboot

---

### Post by gvoima on 2010-06-07
To install the default packages that was there when you installed the OS, use ubuntu-desktop. It's a meta-package that refers to all other default packages, including brasero, compiz etc.
```
sudo apt-get install ubuntu-desktop
```

---

### Post by boonenoob on 2010-06-07
> I would be careful about saying this, it is a whole os that could have  irreplaceable stuff on it. Does this make sense to you? No offers of  recovery and just replace is not very helpful.
sorry. to me it looked like he completly broke his OS, but upon second reviews of his post, I can see that the situation may not be as severe. try reinstalling the packages like the above post tells you to.
sorry for jumping to conclusions.

---

### Post by Cant on 2010-06-07
> **boonenoob said:**
> completly broke his OS
lol

Thanks guys, I'll try sudo apt-get install ubuntu-desktop

---

### Post by Barafu Albino Cheetah on 2010-06-07
Linux is greate for _not_ having irreplacable stuff. Unles specifically created. 
Just install packages back. Don't forget to restart. 
Tried to remove pidgin from Synaptic. No disastreous consequences. It seems you have additionally clicked wrong package for deletion. 
Be really carefull with linux. Simple mistake like this
[B]DON'T TRY THIS AT HOME
[/B]```
rm -rf /home /user001123 /Videos /BoringAds.avi
```can cost you more, then a ruined day. Do you even see an error?

---

### Post by howefield on 2010-06-07
> **Barafu Albino Cheetah said:**
> Tried to remove pidgin from Synaptic. No disastreous consequences. It seems you have additionally clicked wrong package for deletion.

Depends on the Ubuntu release (s)he is using.

If it is earlier than 9.10, then it would have been possibly well integrated into the desktop, obviously not so much now that it is no longer a default application.

---

### Post by Cant on 2010-06-07
I have another problem. I can't connect to the wireless network here. I'm suppoused to this:
```
iwconfig eth1 ap (ap mac address)
iwconfig eth1 essid (name of router)
iwconfig eth1 key s:passphrase
dhclient eth1
```
Right?

When I type "iwconfig eth1 ap (adress)" all I get is "iwlist: command 'ap' needs fewer arguments (max 0)

---

### Post by wilee-nilee on 2010-06-07
> **boonenoob said:**
> sorry. to me it looked like he completly broke his OS, but upon second reviews of his post, I can see that the situation may not be as severe. try reinstalling the packages like the above post tells you to.
sorry for jumping to conclusions.

No problem it is easy to just post an answer, I do it all the time usually in the cafe that is well, not needed. But when it comes to a whole OS or a situation where it can be lost I try to be very careful not to overstep my limited knowledge and let the people who know the fix take care of it. ;)

We have to consider that sometimes people will follow advice that is not correct due to the stress of a broken setup, and just make things worse.

---

### Post by jwbrase on 2010-06-07
> **Barafu Albino Cheetah said:**
> Simple mistake like this
[B]DON'T TRY THIS AT HOME
[/B]```
rm -rf /home /user001123 /Videos /BoringAds.avi
```can cost you more, then a ruined day. Do you even see an error?

Yup. Inserting spaces into a directory path will do that.

---

### Post by sandyd on 2010-06-07
> **jwbrase said:**
> Yup. Inserting spaces into a directory path will do that.
thats why we use tlides. It means we will only do damage to our own home folder :D

---

### Post by Cant on 2010-06-07
> **Cant said:**
> I have another problem. I can't connect to the wireless network here. I'm suppoused to this:
```
iwconfig eth1 ap (ap mac address)
iwconfig eth1 essid (name of router)
iwconfig eth1 key s:passphrase
dhclient eth1
```Right?

When I type "iwconfig eth1 ap (adress)" all I get is "iwlist: command 'ap' needs fewer arguments (max 0)
:-|

---

### Post by angry_johnnie on 2010-06-07
not sure, but if you can get a wireless connection from your ubuntu live cd, you could boot from it, and then chroot into your current ubuntu partition, and then reinstall ubuntu-desktop.

so, that would be something like

```
sudo chroot /your/partition

apt-get install ubuntu-desktop
```

again, i'm not sure it'll work.  i'm not sure it'll set the proper permissions, but it's worth a try.

---

### Post by cbecker78 on 2010-06-07
> **angry_johnnie said:**
> not sure, but if you can get a wireless connection from your ubuntu live cd, you could boot from it, and then chroot into your current ubuntu partition, and then reinstall ubuntu-desktop.

so, that would be something like

```
sudo chroot /your/partition

apt-get install ubuntu-desktop
```again, i'm not sure it'll work.  i'm not sure it'll set the proper permissions, but it's worth a try.

At the very least, its worth dropping a live cd in and backing up your /home before you go any further... just in case things get worse rather than better.  

Now I'm not sure about the next bit, but if you add the ubuntu CD back to your sources.list, you may be able to apt-get update and install ubuntu-desktop that way.  If what I just said makes sense, someone else can probably give full instructions on how to do it.  Though I could try to hack my way through the steps for you if you have run out of other options and want to give it a try.

---

### Post by angry_johnnie on 2010-06-07
> **cbecker78 said:**
> Now I'm not sure about the next bit, but if you add the ubuntu CD back to your sources.list, you may be able to apt-get update and install ubuntu-desktop that way.

you know, you're right about that... :)

if your computer boots into a command line login, then just log in with your usual username and password.

insert the cd.

then do this:

```
sudo nano /etc/apt/sources.list
```

the ubuntu cd should already be there, at the very top, commented out.

so, all you need to do is uncomment the entry (remove the ## signs).  Then, comment out everything else (add ## signs at the beginning).

then do
```

sudo apt-get update

sudo apt-get install ubuntu-desktop
```


also:

if your cd/dvd rom is not mounted for any reason, you could try:

```
wodim --devices 
```

note the output should be something like /dev/sdX (where sdX could actually be hdX or scX or whatever)

create this directory if it does not exist already:
```

sudo mkdir /media/cdrom0 
```

then

```
sudo mount -t iso9660 /dev/sdX /media/cdrom0/ 
```

---

### Post by Cant on 2010-06-11
I keep trying to do "sudo apt-get install ubuntu-desktop" but I always get an error saying "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
:x

Also: When I try to run "dpkg --configure -a" I get a message saying "requested operation requires superuser privilige"
:x

---

### Post by helliewm on 2010-06-11
Run the command 'dpkg --configure -a' just type it into the Terminal and press enter. Then try again with sudo apt-get install ubuntu-desktop

Helen

---

### Post by Cant on 2010-06-11
> **helliewm said:**
> Run the command 'dpkg --configure -a' just type it into the Terminal and press enter. Then try again with sudo apt-get install ubuntu-desktop

Helen

That might be a problem.

[quote=Cant]Also: When I try to run "dpkg --configure -a" I get a message saying "requested operation requires superuser privilige"[/quote]

---

### Post by helliewm on 2010-06-11
Apologies I should have said type " sudo dpkg --configure -a" into the Terminal and press enter. It will ask for your password type it in and press enter.

When its finished try again with with "sudo apt-get install ubuntu-desktop"

Helen

---

### Post by Cant on 2010-06-11
> **helliewm said:**
> Apologies I should have said type " sudo dpkg --configure -a" into the Terminal and press enter. It will ask for your password type it in and press enter.

When its finished try again with with "sudo apt-get install ubuntu-desktop"

Helen

I still get the "dpkg: requested operation requires superuser privilige"

---

### Post by helliewm on 2010-06-11
sudo is the superuser privilege. It effectively means you are root. Try again 
type the following exactly as here:

sudo dpkg --configure -a

It will ask for your password. Type it in and press enter.

Helen

---

### Post by Cant on 2010-06-11
> **helliewm said:**
> sudo is the superuser privilege. It effectively means you are root. Try again 
type the following exactly as here:

sudo dpkg --configure -a

It will ask for your password. Type it in and press enter.

Helen

**** YEAH

IT WORKED

Thank you, Helen :guitar:

---

### Post by robsoles on 2010-06-11
> **Barafu Albino Cheetah said:**
> Linux is greate for _not_ having irreplacable stuff. Unles specifically created. 
Just install packages back. Don't forget to restart. 
Tried to remove pidgin from Synaptic. No disastreous consequences. It seems you have additionally clicked wrong package for deletion. 
Be really carefull with linux. Simple mistake like this
[B]DON'T TRY THIS AT HOME
[/B]```
rm -rf /home /user001123 /Videos /BoringAds.avi
```can cost you more, then a ruined day. Do you even see an error?

LOL, don't make too many spaces, what a nightmare - you gonana delete "/home/" (everyone's crap), "/user001123/" (someone's crap), "/Videos/" (probably doesn't actually exist), and "/BoringAds.avi" (betcha definitey doesn't exist if ask 'ls /BoringAds.avi' before 'remove' command) - ouch, ouch, ouch - always do something harmless to files before you 'rm -Rf' them - more a matter of the -f but wouldn't hurt as much without the -R !!!!

LOL, sorry - a little drunk and looking around, prolly shouldn't post in this state but can't stop chuckling really!

To do right thing to topic: Yeah, checking history or pursuing "sudo apt-get install ubuntu-desktop" are best responses to problem posed!!!! (LOL, chuckle, gag, etc, prolly-not-apt, LOL, better stop!!! :lolflag:!)

---

### Post by helliewm on 2010-06-11
Is the UBuntu-desktop reinstalling itself now I assume you have now been able to to type the following into the Terminal?

sudo apt-get install ubuntu-desktop 


Helen

---

### Post by robsoles on 2010-06-11
> **Cant said:**
> **** YEAH

IT WORKED

Thank you, Helen :guitar:
So it should have, please tell everyone you are on a real pretty GUI (graphical, pictures and all, User Interface) so they can relax and quit stressing you might be lovin' Ubuntu less than you ought!!!!

EDIT: Goodnight! (sorry if I broke the convo up with nonsense really, loved this thread but!)

---

### Post by BoneKracker on 2010-06-11
I don't use ubuntu, but it sounds to me like they ought to relabel "remove completely" to something else.

"Remove completely" doesn't exactly express the idea that it's going to remove everything that depends on this package.  It sounds more like its going to remove everything this package depends upon that's not needed by something else (which would be a sane action.

Instead of gutting the system of everything that depends on this package, the package manager ought to simply point out the unsatisfied dependencies the next time it resolves them, and offer to reinstall the missing dependency.

Rapaciously expunging a whole tree of reverse dependencies from a system is not something a user will often want to do, and it shouldn't be that easy to do it.

---

### Post by robsoles on 2010-06-11
> **BoneKracker said:**
> I don't use ubuntu, but it sounds to me like they ought to relabel "remove completely" to something else.

"Remove completely" doesn't exactly express the idea that it's going to remove everything that depends on this package.  It sounds more like its going to remove everything this package depends upon that's not needed by something else (which would be a sane action.

Instead of gutting the system of everything that depends on this package, the package manager ought to simply point out the unsatisfied dependencies the next time it resolves them, and offer to reinstall the missing dependency.

Rapaciously expunging a whole tree of reverse dependencies from a system is not something a user will often want to do, and it shouldn't be that easy to do it.

Honestly going to bed in a couple of minutes, just waiting to see if OP will state they are back in nice GUI - Sorry to think I understand what you have stated (ie., in my current state) :

Has someone posted a bug report over this coz my take on what you said makes me think it's actually a bug, a very nasty one at that too (not one that would get me in any state, let alone current one, but one that I could easily imagine getting any one of my 'friends'!!!)

Perhaps at least it should be a 'wishlist' type of bug - I promise I am not stopping for another post tonight!!!!

EDIT: Geez you use complicated construction BoneKracker, I'd love it if I wasn't so c'cked up right now!!! (LOL) (eg, rapaciously - think it must be based loosely on the word 'rape' (ouch, that hurt my head - making the connection)).

---

### Post by BoneKracker on 2010-06-11
> **robsoles said:**
> Has someone posted a bug report over this coz my take on what you said makes me think it's actually a bug, a very nasty one at that too
I don't think it's a "bug" per se, just questionable design decisions.

---

### Post by Cant on 2010-06-11
> **BoneKracker said:**
> I don't think it's a "bug" per se, just questionable design decisions.

I second that.

---

### Post by robsoles on 2010-07-02
> **BoneKracker said:**
> I don't think it's a "bug" per se, just questionable design decisions.

I was a little drunk when I posted what I posted to be replied like this but being a little drunk again I think to say:

Questionable design decisions amount to bugs in my book and if I wrote the code behind this one and someone complained I would treat it like a bug in my fervor to make it better!

---

### Post by d3v1150m471c on 2010-07-02
ouch... yeah part of that was user error but removing pidgin shouldn't have caused this. here's hoping someone who develops the packaging system notices the thread

---

