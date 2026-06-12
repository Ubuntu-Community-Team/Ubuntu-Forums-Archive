---
title: "Install Ubuntu without a monitor."
date: 2011-09-05
forum: General Help
---

### Post by Juma92 on 2011-09-05
I'm having trouble installing ubuntu server on a PC with no monitor.

I have a PC without a keyboard, mouse or monitor that I want to install Ubuntu server on. Since I dont have any way of interacting or seeing the installation process I took the hard drive out of the computer and put it into an external enclosure. I replaced my laptops hard drive with the external enclosure and used the ubuntu server install cd to install the operating system on the external hard drive. The installation went well and I even tested the hard drive on another laptop before putting it back into the original PC without the monitor.

Here is where my problems started. When I booted the hard drive from the my laptops I was easily able to SSH into the system remotely. Both laptops have static ips set in the router and knowing their address was easy. When I plugged the hard drive into the PC without a monitor my router didnt pick it up after it booted and I couldn't access it. 

Is there some way to find the MAC address of the PC without going into the operating system so I can set a static ip for it? And how can I know if my hard drive is booting all the way through and not giving me an error or such?

So now I'm stuck with a PC with an installed operating system on it but no way of accessing it. Looking at my routers active clients I see my laptops, my android and my kindle but not the PC. I have run out of ideas and am not sure what to do! Help me please!

---

### Post by stinkeye on 2011-09-05
I have no experience in this but had filed this away in my linux guides if I ever needed it.
[**_[COLOR="DarkRed"]http://www.ghacks.net/2010/11/28/configure-linux-to-boot-without-a-monitor/[/COLOR]_**]("http://www.ghacks.net/2010/11/28/configure-linux-to-boot-without-a-monitor/")

---

### Post by Juma92 on 2011-09-05
That was very helpful but I thought Ubuntu Server doesnt come with X-Window? So wouldnt that make the irrelevent for me?

---

### Post by mickwombat on 2011-09-05
It sounds like some hardware issues as the OS was installed on a different platform.

Unfortunately, the only way you can troubleshoot this is to connect a monitor temporarily to see what the errors are.  Quite possibly it could be stuck on the bios waiting for you to press F2 or something to confirm changes.

Try to connect it to a monitor or TV just to see that boot screen.

:P

---

### Post by Juma92 on 2011-09-05
I wish I had one but I dont. I've spent all day trying to find alternatives. 

I'm fairly certain my problem is menial and could easily be fixed with a monitor but since I dont have one at my disposal Im forced to look for alternatives.

---

### Post by dougalkerr on 2011-09-05
This is an interesting thread... I can't see how you can tell what is happening without a monitor. Like another said, the BIOS may be waiting for an input from you.
Are you able to do this with other any other operating systems without the problems that you are encountering. I am wondering why you thought you should be able to do this without knowing how the system was going to react when connected to the server unit. There are obvious hardware/processor differences between the laptops and the server unit. Apart from that you could always see what was happening on the laptop screens.
It will be interesting to see what the outcome is if you can do anything without a monitor. Oh, and if the BIOS is waiting for an input, how are you going to do that without hooking up a keyboard if you can't get a Network connection to take control (just a thought).
I don't mean to sound negative at all but, the server guys at work always have a keyboard, mouse and monitor available to get them going. Usually they will use an image that they have created to get the server going but, that does depend upon all the hardware being pretty much the same as the unit they based the image on. You created the image using a laptop, the differences between this and the server unit can be significant.

---

### Post by mickwombat on 2011-09-05
I know with my server being an old HP desktop, whenever things like hard drive or ram is changed it first gives a warning that 'Configuration has change blah blah blah, Press F2 to continue'

Given that it doesn't get an ip from your router, that may be the issue.  I've also seen some older models won't boot up if there is no keyboard attached as well.

Most TVs these days lets you attach a PC, so you can try that.  Unfortunately, no way around this without a monitor/TV.  Once it's sorted, you won't need the monitor again.

:-)

---

### Post by Juma92 on 2011-09-05
Well I tested the hard drive on different hardware and it ran fine (although the other hardware was another laptop, so I dont know how well of a test that was).

I'm pretty sure I've narrowed my problem down to something with the BIOS, the PC never shows up on my ddwrt active client list so it never boots into Ubuntu in the first place. 

I think my next course of action is to reset the BIOS by removing the motherboard battery. Hopefully that will default the boot order and boot me into the hard drive and fix my problems.

I knew from the start that I would run into trouble with this but without a monitor on hand I had no other choice. Oh well this will surely be a learning experience for me.

---

### Post by mickwombat on 2011-09-05
resetting the bios probably won't help.  It's unlikely to be the boot order as it should eventually boot from the hard drive.

You just need to save yourself the frustration and take it into work and borrow a monitor in your lunch break.

Boot the drive again using the laptop and post the output of 


```
cat /etc/fstab
sudo blkid
```

---

