---
title: "Dell Dimension 4600"
date: 2012-08-31
forum: General Help
---

### Post by joco1500 on 2012-08-31
Hello, 
my school has recently cleaned out the computer lab because they are moving to apple computers.

I tried to tell them to just put Ubuntu on the old dells but they wouldn't listen. 

i got one of the dells for $50.

now i was wondering what the best *buntu was for it.

sorry because i don't know any of the specs on it.

---

### Post by aspidistra on 2012-08-31
> **joco1500 said:**
> Hello, 
my school has recently cleaned out the computer lab because they are moving to apple computers.

I tried to tell them to just put Ubuntu on the old dells but they wouldn't listen. 

i got one of the dells for $50.

now i was wondering what the best *buntu was for it.

sorry because i don't know any of the specs on it.

i've got a dimension 8300 which is about the same year - box looks the same
very reliable machine has been robust mainstay for many years

currently most reliably (totally, even for work) running xubuntu 10.04
that machine only has 500mb of RAM

I can't run 12.04 atm because I have issues with it, but it'd probably be just as fast

rule is for an older machine like that - xubuntu
I know it's fast because I have certain graphical programs of game runs excellently

when you see older machines such as the one you have scored (is from 2003)
on ebay - you will see they generally have xubuntu installed on them

10.04 is an LTS (long term support version) of ubuntu - currently 10.04 is still supported until next year 

12.04 is another LTS version which will probably be supported until 2015?  will be on the wikipedia article ...

both of those xubuntus run xfce.  xfce is what fedora currently ships with 

xfce4 ships on 12.04 xubuntu - the prior to that version (on 10.04) is very basic (but simple) - just takes longer to set up

xfce4 is more luxurious, complete.

I go with xubuntu because I know where everything is (menued) .. I have no desire to use unity.  stopped using pure ubuntu when it all went to unity.  I don't run mobile apps or anything funky - I just want a simple gnome like desktop menu interface where I know everything is

also the panel - most common question I have seen on freenode #ubuntu irc is "where is the panel?" how do I get the panel back.  

xubuntu is similar to pre-unity ubuntu - just pull it down install from cd /dvd or usb key (I format a usb key using the program "usb-creator-gtk" (blank it, then format it using the large downloaded .iso file).

then to get it going (I use a wireless usb adapter such as netgear wg511)

go to system > software sources (from menu) .. then "other software" tab - click into tick box "canonical" to ensure you get all the updates 

then system "update manager" to get roughly now 220mb of updates down

then I generally turn off screen saver then set up "settings" power management to stop the screen turning off

apart from getting nfs etc working or ssh

btw - the very 1st thing you should do before connecting is enable firewall

"sudo ufw enable"

then "sudo apt-get install ubuntu-restricted-extras" will get your video/flash working

... on an old machine like that video may be an issue.  you may find youtube for example plays better using chrome .. all round you will find chrome to be a faster experience than firefox 

good luck

I have tried lubuntu - but had some issues with it
I know it's even lighter weight (less ram needed, processor) then xubuntu
lubuntu is a main stream release now

but it's not xfce or gnome it's some more obscure window manager 
which was 1 reason I stayed away
have tried them all man ... viva ubuntu!  many choices

---

### Post by fabietto0102 on 2012-08-31
and even lighter than Xubuntu is Lubuntu. I believe it's the lightest of the buntu's family. 

Alternatively, download and install ubuntu minimal and take it from there...

---

