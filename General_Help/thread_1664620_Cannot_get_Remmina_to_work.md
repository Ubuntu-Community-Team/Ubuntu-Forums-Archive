---
title: "Cannot get Remmina to work"
date: 2011-01-11
forum: General Help
---

### Post by priteshj on 2011-01-11
Hello,

I'm new to Ubuntu and need to be able to remote desktop to Windows 2008 servers to provide support to my company(preferably from my Ubuntu laptop so that I can get rid of windows). I tried RDP but was not happy with it. I found a product called Remmina and after spending some time on google I found the following command to install in on Ubuntu 10.10:

sudo apt-get install remmina

Then I tried launching it from the menu item and nothing happened. I then tried running it from the command line: /usr/bin/remmina and I get the following error:

Remmina plugin RDP (type=Protocol) registered.
Remmina plugin RDPF (type=File) registered.
Remmina plugin RDPS (type=Tool) registered.
xkbLayout: za    xkbVariant: 
Segmentation fault

I also tried installing as follows:

sudo apt-get install remmina remmina-plugin-data remmina-plugin-nx remmina-plugin-rdp remmina-plugin-telepathy remmina-plugin-vnc remmina-plugin-xdmcp

Still getting the Segmentation fault error.

Has anyone else experienced this? Any suggestions on how to fix?

Thank you

Regards
Pritesh

---

### Post by spietkop on 2011-03-01
Running Maverick 64 bit and had the same issue,so looking at the problem closer:
xkbLayout: za    xkbVariant: 

Points me to a keyboard layout issue, so I changed it to US,
I then removed the South Africa layout and added United Kingdom

How?
System, Preferences, Keyboard
Add button is found under the LAYOUTS tab

Rebooted my laptop and it was working.

---

### Post by Sidster on 2011-06-08
Hey there fellow South Africans

This fix isn't working for me on Natty

Every time I remove the ZA layout it just comes back after a reboot. I think a more permanent solution would be to notify the developer or submit a bug report on launchpad

I don't have the time now but will probably get to it this week sometime.

---

### Post by Sidster on 2011-06-09
I've logged the bug on Launchpad and will start a thread on the remmina forums

Launchpad bug [#794415]("https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/794415")

---

### Post by AcidHawk on 2011-12-09
Still no news on this .. 

I am getting the problem in 11.10 also - about to try the keyboard change from za to us ...

---

### Post by AcidHawk on 2011-12-09
Nope ... still doesn't work!

changed my Keyboard to US and to UK but still no luck.

Remmina still gets a seg fault.

I hope they sort this out some time soon .... :(

---

### Post by eugenevdm on 2011-12-12
Same problem here ZA Keyboard, we tried changing Keyboard Layout, it remembered the US layout, but Remmina segfault.

---

### Post by priteshj on 2012-01-15
I had this working under Ubuntu 10.10 just after I posted the initial problem in Jan 2011. Now a year later I decided to reinstall my T61 with 11.10 and the dreaded segmentation fault error is back :confused:. Is this problem only affecting South Africa keyboard users? Has anyone else got this to work.

Thank you
Pritesh

---

### Post by eugenevdm on 2012-01-16
I hope we get this sorted. My users can't perform a backup to flash because of this issue. Only Remmina was the client that could connect to a remote store.

---

### Post by Trance101 on 2012-03-05
Hi,

I managed to find a workaround to this. You can edit your XkbLayout in the following file: /etc/default/keyboard

```
$ gksudo gedit /etc/default/keyboard
```

Then change XKBLAYOUT="za" to XKBLAYOUT="us". After this you will need to reboot and Remmina should start.

---

### Post by oregonbob on 2012-03-07
I have the exact same error only I am in the US and am already using US keyboard. At one time I had remmina working but somehow broke it. I now can remove everything Remmina, reinstall from Synaptic and still the the error:

Protocol plugin RDP not installed.

If I run it as root, it will not even allow a new connection to use RDP, only SSH.

---

### Post by PhilGil on 2012-03-07
> **oregonbob said:**
> I have the exact same error only I am in the US and am already using US keyboard. At one time I had remmina working but somehow broke it. I now can remove everything Remmina, reinstall from Synaptic and still the the error:

Protocol plugin RDP not installed.

If I run it as root, it will not even allow a new connection to use RDP, only SSH.

Do you have the "remmina-plugin-rdp" package installed? If it isn't available in the Software Center you'll need to activate the Universe repository.

---

### Post by oregonbob on 2012-03-07
> **PhilGil said:**
> Do you have the "remmina-plugin-rdp" package installed? If it isn't available in the Software Center you'll need to activate the Universe repository.

Yes, that is installed. I also tried debs from a [PPA]("https://code.launchpad.net/~freerdp-team/+archive/freerdp/+packages") and got that same error: "Protocol plugin RDP not installed".

---

### Post by oregonbob on 2012-03-07
I got mine to work. I am now running the new version from PPA.

It turned out somehow I had a 2nd copy of binary remmina in /usr/local/bin. I removed that copy and it all works! So the new Remmina was not being accessed.

I am now running version 1.0.0-3~405+13~oneiric1 on my 11.10. It is a PPA by "chihchun". They made a bunch of nice improvements too.

---

### Post by PhilGil on 2012-03-07
Never mind; glad you got it working.

---

### Post by strid3r on 2013-01-04
> **oregonbob said:**
> I got mine to work. I am now running the new version from PPA.

It turned out somehow I had a 2nd copy of binary remmina in /usr/local/bin. I removed that copy and it all works! So the new Remmina was not being accessed.

I am now running version 1.0.0-3~405+13~oneiric1 on my 11.10. It is a PPA by "chihchun". They made a bunch of nice improvements too.

Great, I was just about to update remmina when I remembered that I had copied the ~/.remmina folder from 12.04 (I'm on 12.10) 

So I just ran ```
rm -rv ~/.remmina
``` in the terminal and everything works fine now.

---

