---
title: "Is there a Network Setting in Jaunty Jackalpoe?"
date: 2009-09-12
forum: General Help
---

### Post by ozguitarplayer on 2009-09-12
Hi,
Where do I find something like the application Network Setting so I can add a host with ip address?
I'm sure there is one however I can't find it.
Using Jaunty Jackalope with GDE

---

### Post by ithinkitschad on 2009-09-12
> **ozguitarplayer said:**
> Hi,
Where do I find something like the application Network Setting so I can add a host with ip address?
I'm sure there is one however I can't find it.
Using Jaunty Jackalope with GDE

Is it a fresh install? Maybe at the top right? Thats where it should be. You left a very  vague question. I'm a gypsy that can see through time/and peoples minds. But alot of people cant. Maybe leave a lil more info.

***
sys specs
 distro
wifi card
***

at the least

---

### Post by stderr on 2009-09-12
As ithinkitschad indicated, you haven't made what you want to do very clear... are you trying to add a (host, IP address) pair for local DNS resolution? If so, that's the job of the file /etc/hosts.

```
gksudo gedit /etc/hosts
```

---

### Post by ozguitarplayer on 2009-09-12
I was vague & that's because I can only vaguely remember. I know with other Ubuntu installations that was an icon one the panel ithinkitschad mentioned this and reminded me.

And yes I am trying to add a (host, IP address) pair for local DNS resolution. 

I wouldn't know what to enter in /etc/hosts this is why I need to find the GUI version. In Debian GDE it's Places > Admisistration > Network and this brings up a Network Settings window with Connections, General. DNS and Hosts tabs.

I have four computers set up.
What would I enter if I did try to edit /etc/hosts? 
Just the IP addresses?
Can I give the IP address a names to make it easier to tell them apart?

---

### Post by falconindy on 2009-09-12
/etc/hosts/ should have some entries in it already that will give you an idea of what to enter. In case it doesn't, it's just in the form of something like this:
```
8.10.77.140    seraphic-.deviantart.com
```Damned deviantart and their non-compliant machine names.

Make sure you edit the file as root. Changes take affect as soon as its saved.

---

### Post by stderr on 2009-09-12
If you're running NetworkManager, then through System->Administration->Network's Hosts tab, you should be able to do what you want. However, I really would just edit /etc/hosts if I were you. The format is 

IP address [some whitespace] hostname

which is simpler than what you'd enter through a GUI anyway. Just use the command I gave you before to open the file in a nice & simple text editor, and follow the examples of what's already there. How much whitespace you use doesn't matter. Just hit tab a couple times if you like, or try and match the whitespace already used in previous lines to be neat ;)

edit: TBH, an easier way would simply be to avoid using a GUI at all and just use:

```

echo "192.168.1.10 myhostname" | sudo tee -a /etc/hosts > /dev/null

```

---

### Post by ozguitarplayer on 2009-09-13
Thanks heaps everyone, wonderful support. 
I got it sorted in /etc/hosts.

FYI I found what I started out looking for in one of my other computers with Hardy installed and it was in the same place as Debian i.e. System > Administration > Networking. 
And although synaptic tells me I have Network Manager installed there is nothing in System > Administration that is Networking or Network's Hosts in my Jaunty. 
I have checked in System > Preferences > Main Menu

---

### Post by pi_31415926535898 on 2009-09-25
Along the same lines as the OP, I am looking for a way to identify a particular network (wireless, in my case) with a specific hosts entry. I upgraded from Hardy (via a brief stop at Intrepid) a few days ago, and in Hardy I could specify my 'location,' which would bind an internal IP address to my domain (when I was at home), or would unbind the address (when I was at school).

My question, then, is whether there is a feature in Jaunty which is roughly equivalent to its Hardy counterpart, such that I don't have to manually edit the hosts file every time I change locations (or build a script to manage this for me). It's a hell of a lot easier to tell the system, 'I am [here],' and have it automatically assign the appropriate hosts entry for my domain(s).

I neglect to offer specs other than distro, as they are irrelevant to the question; I am running Jaunty.

Thanks!

--
Stan

---

