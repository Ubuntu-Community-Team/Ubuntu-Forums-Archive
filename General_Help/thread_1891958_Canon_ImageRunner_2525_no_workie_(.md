---
title: "Canon ImageRunner 2525 no workie :("
date: 2011-12-06
forum: General Help
---

### Post by cbanakis on 2011-12-06
So, I'm trying to get the printer at my office (Canon ImageRunner 2525) to work with my laptop (Ubuntu 11.04)

I got a deb package from [http://software.canon-europe.com/products/0010803.asp](http://software.canon-europe.com/products/0010803.asp)

Installed without any problems, Ubuntu detected the network printer, and selected the appropriate driver that was installed by the deb.

No errors of any kind during setup, or when attempting to print.

Documents go through all the motions of printing without a hitch.

But then when I get my lazy but up, and walk down the hall to the printer, nothing is there.

I checked the printers history (physically, on the printers touch-pad), and there is no record of ever receiving the job.

All the other computers at my work are Mac, or Windows, and the printer works fine on them.

Ive had trouble with finding drivers before, but never have I found the correct one, and it still didn't work.

Any ideas?

Has anyone dealt with this specific printer before?

Thanks in advance.

---

### Post by phidia on 2011-12-07
I checked at openprinting.org and the model you listed doesn't show there.
That's not a good sign unless you entered the model incorrectly?

I found an [imagerunner 2550]("http://www.openprinting.org/printer/Canon/Canon-imageRunner_C2550") which is said to work "mostly"

You might be able to find some helpful resources at that site.

---

### Post by cbanakis on 2011-12-07
The model is correct.

Why would there be an available driver if it does not work?

Seems like an unusual waste of time for canon to make a driver that serves no purpose.

I guess I'll try the 2550 driver and get back to you.

Thanks for the post.

---

### Post by cbanakis on 2011-12-07
no luck using the 2550 driver. Same exact result.

I am so confused by this.

Why would there be a driver if it does not work?

---

### Post by cbanakis on 2011-12-08
I am completely at a loss.

Am I mistaken about the driver I downloaded?

It says imagerunner2525, and it is for Ubuntu.

Is there maybe a workaround I can try?  (Sharing the printer on a mac or windows machine?)

---

### Post by cbanakis on 2011-12-09
*Bump

---

### Post by Azdour on 2011-12-09
Hi,

Just a guess but it looks like CQue has a GUI which you may need to use to install the printer through. Like HP has hp-setup and Samsung has their own GUI.

See - [http://www.franet.com/nprodCQueE.php](http://www.franet.com/nprodCQueE.php). I've had a quick look but I have not found out how to launch the CQue GUI or how to add a printer, but maybe this will help you?

---

### Post by cbanakis on 2011-12-09
> **Azdour said:**
> Hi,

Just a guess but it looks like CQue has a GUI which you may need to use to install the printer through. Like HP has hp-setup and Samsung has their own GUI.

See - [http://www.franet.com/nprodCQueE.php](http://www.franet.com/nprodCQueE.php). I've had a quick look but I have not found out how to launch the CQue GUI or how to add a printer, but maybe this will help you?

Thanks for the input.

I got into the GUI, apparently, you just type "cque" in terminal.

Still no luck though, lots of options in the GUI.

This could take some tinkering.

Hopefully it is possible to get this working eventually.

---

### Post by cbanakis on 2011-12-09
This printer is gonna be the end of me.

As far as I can tell, using the cque GUI has the same results as simply adding the printer in ubuntu's printer manager.

everything works fine, except for actually printing something.

There has to be someone out there who has got this to work.

---

### Post by cbanakis on 2011-12-16
Nobody has successfully used this driver and printer?

---

### Post by cbanakis on 2011-12-19
*Bump

---

### Post by rogerdefl on 2011-12-21
try this, worked for me.
[http://disbauxes.upc.es/?p=3434](http://disbauxes.upc.es/?p=3434)

---

### Post by cbanakis on 2011-12-21
Thank you very much for the post, but the results seem to be the same.

I am curious about the comment on the linked page 
"- Be careful with your iptables configuration."

Not sure what that means?
Could that have something to do with the problem?

I just don't understand, everything seems to work perfect except for actually printing.

I can connect directly to the printer via IP, and see all the stuff everyone else has printed, but for some reason I cannot get anything from my computer to the printer.

> **rogerdefl said:**
> try this, worked for me.
[http://disbauxes.upc.es/?p=3434](http://disbauxes.upc.es/?p=3434)

---

### Post by cbanakis on 2011-12-27
Tried upgrading to 11.10 (Unity)

Thought maybe this was a problem with natty, but no.

Just wasted a bunch of time, especially since I then had to downgrade back to natty, cause I hate Unity.

---

### Post by cbanakis on 2011-12-28
*Bump

---

### Post by watgrad on 2011-12-28
I had networking printing problems a while ago - I was able to solve by opening port 631 for printing in the firewall configuration utility...

---

### Post by cbanakis on 2011-12-29
Brilliant idea, but it did not help.  :(

Thanks for trying though.

I just found something else in CUPS.

Under Default Options...

If I click on "Query Printer For Default Options"

The Result Is

[Unable to send command to printer driver!
  [INDENT]Unsupported format 'application/vnd.cups-command'!]
[/INDENT]

---

### Post by 1clue on 2011-12-29
Go to one of the working Macs, and find out what the driver is called.

For me, I have a Canon MF8050Cn which uses a UFRII driver.  Same name on the mac.

There is a thread, [http://ubuntuforums.org/showthread.php?t=1723101](http://ubuntuforums.org/showthread.php?t=1723101) which has some info that might be useful.  Also it helped for me to remove the model number of the printer and just describe what the printer is, such as 'Canon all in one laser printer' and it got me more results.

---

### Post by cbanakis on 2011-12-29
AHA!!!!

So...

I followed your link to the other forum, and found this.
[http://ubuntuforums.org/showpost.php?p=10657848&postcount=5](http://ubuntuforums.org/showpost.php?p=10657848&postcount=5) 

He has all the compatible printers listed in his post. 
Among them is  imageRUNNER2525/2525i/2530/2530i.  (Which is what I have)

I found the file he mentioned.  (o1113enx_l_ufr220.zip)  at  [http://software.canon-europe.com/software/0040355.asp](http://software.canon-europe.com/software/0040355.asp)

Strangely, my printer is not listed under this driver pack on Canons website? 

But I followed  Bagh33ra's instructions, and installed that driver pack (Instead of the one Canon says works with my printer?)
And after a couple minutes of tinkering...

**VUALA!!!**

Thank you all for your help.

---

