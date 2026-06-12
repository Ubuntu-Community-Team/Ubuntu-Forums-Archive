---
title: "Changed from Mint to Ubuntu now can't print"
date: 2010-04-22
forum: General Help
---

### Post by raybarrow on 2010-04-22
Hi Folks,
Apologies if this appears twice. Posted this morning but can't find any trace of it?

Desktop PC Dual boot XP/Linux Mint
Laptop was Dual boot Vista/Linux Mint.

Changed my Laptop set up from dual boot Vista/Linux Mint 8 to Vista/Ubuntu 9.10.

I have two printers one of which (Canon BJC300) is physically connected to the Desktop PC. The other is netorked through a wireless router. Worked find with Samba/Cups in Linux Mint. Can't get it to work with Ubuntu. (Linux Mint is based on Ubuntu).

Desktop PC Name is "pcname"
Desktop PC Workgroup is "pcworkgroup"
Printer Name is "Canon BJC 3000"
Not really but they'll do for the demo.

Set up printer in Ubuntu smb://pcworkgroup/pcname/Canon BJC 3000

Appears to accept it that but doesn't print. Times out with 'printer unaccessible'.

Where do I need to concentrate my efforts?

Are there some permissions I've overlooked. I haven't altered anything on the Desktop PC.

Cheers,
Ray.

---

### Post by Morbius1 on 2010-04-22
What's not clear in your description is whether you are trying to connect to that printer when it's attached to the machine when it's running Windows or Linux.

If it's running Windows then:
> smb://pcworkgroup/pcname/Canon BJC 3000looks right although I'm not sure about the spaces in the printer name. Even when I ran an all Windows network I always eliminated spaces in share names. Perhaps this will work, I just don't remember how linux handles spaces in this type of situation:

```
smb://pcworkgroup/pcname/Canon\040BJC\0403000
```Substitute \040 for spaces in the name.

If it's running Linux don't go through samba:
```
ipp://pcworkgroup/pcname:631/printers/Canon BJC 3000
```Once again, for the life of me I don't remember how it handles spaces so it might be:
```
 ipp://pcworkgroup/pcname:631/printers/Canon\040BJC\0403000
```I guess the best approach to avoid confusion is to change the printer name to Canon3000 :wink:

---

### Post by raybarrow on 2010-04-23
Hi Morbious 1,

Yes, I wasn't very clear on the setup was I?

Desktop PC is XP/Linux Mint dual boot. It's the family one so it runs Windows XP most of the time, including when I'm trying to connect to the Canon printer which is attached to it via parallel port.

My laptop runs Vista/Ubuntu (just changed from Mint) and only connects to anything via the wireless router.

Tried your suggestions and nothing. Samba appears to see my 'pcworkgroup' and 'pcname' but won't make that final leap to the printer.

I think I might reinstall Linux Mint and hopefully, if it connects, note the settings. It's just strange that I did it in Mint, which is Ubuntu based, but not in Ubuntu. I think I'm missing something obvious, but hey, a good night's sleep may help my remaining brain cells do their job.

The great thing about Linux is that it's only half an hour's job to do a clean reinstall the OS and programmes.

---

### Post by john newbuntu on 2010-04-23
Did you try going to system->administration->printing.  Click on add new.  Then choose network printer and windows printer on samba. Click browse on the right panel and see if you can spot your windows printer.  Select it if you can and authenticate if necessary.

---

### Post by raybarrow on 2010-04-23
Hi,

Yes, I followed the System>Administration>Printing Config route. The Windows/Samba option detects my Desktop Workgroup and PC name but doesn't see the printer. The Desktop PC and the printer are both switched on.

It's bizarre. I've just running a USB stick Linux Mint on my laptop at the moment to see if that will see it, like it did for several months now, but it doesn't. I've been printing for a good while (prior to the change), so it's not that it can't, it just doesn't want to.

I'm sure I'm missing something really basic.

Thanks,
Ray.

---

### Post by john newbuntu on 2010-04-23
Let me ask a stupid question here.  Is the file and printer sharing for microsoft networks enabled on the desktop PC that is connected to the printer? And in the sharing tab, have you enabled sharing?  Are there any firewalls on Ubuntu that are preventing the share?

---

### Post by raybarrow on 2010-04-23
At this stage there aren't any stupid questions. Yes File/Printer sharing is enabled. No Firewall in Ubuntu.

My firewall on Desktop is set to allow my Laptop via MAC Address.

Just noticed when I look at My Network places in Windows, I can't see my Ubuntu Laptop. The My Network is working OK as I can see my wife's Vista Laptop. We're having a laptop morning to take her mind off things as we're off to the dentist in a little while (she does not like dentists - or rather what they do).

When we come back I'll make sure I can see the Laptop when it's running Vista.

Thanks for your persistence,
Ray.

---

### Post by Morbius1 on 2010-04-23
An even "stupider" question while I stall for time to come up with a real answer :wink:

>  My firewall on Desktop is set to allow my Laptop via MAC Address.
You do realize that the laptop has 2 MAC address, right? The wired MAC address and the Wireless MAC address. Is it possible it's pointing to the wired one only?

---

### Post by raybarrow on 2010-04-23
Again a sensible question, but yes I have both the wired and the wireless MAC addresses allowed.

I can see the Laptop running Ubuntu from the Windows XP Desktop and I can see the Windows Network in the Ubuntu File Browser on the Laptop and get to the PCWorkgroup folder but if I try to go further, to the PCName, I get an 'Unable to mount location. Failed to retreive share list from server' message.

Cheers,
Ray.

---

### Post by john newbuntu on 2010-04-23
Are you sure you are not running gufw/ufw?
Type "ufw" on the command line and disable it for a few minutes and see if it helps.  Or if you have the gui "gufw" under system->admin->firewall configuration, open and disable it.

If not, go through these posts, who had the same problem as you have.
[http://ubuntuforums.org/showthread.php?t=1082148&page=9](http://ubuntuforums.org/showthread.php?t=1082148&page=9)

---

### Post by raybarrow on 2010-04-25
Sorted it. After searching and reading your helpfull replies I tried smb://192.168.1.108/printername.

That's the IP address of my Desktop PC with the printer attached.

Why it wouldn't use the workgroup/name/printername I don't know.

Anyway thanks for all the help.
I can relax and then move on to the next challenge.

Do I have to show the problem 'solved' somewhere, I wouldn't know how to? 

Cheers,
Ray.

---

### Post by Scunnered on 2010-04-25
You will find SOLVED in the thread tools.  It is always appreciated when a post is marked accordingly.

---

