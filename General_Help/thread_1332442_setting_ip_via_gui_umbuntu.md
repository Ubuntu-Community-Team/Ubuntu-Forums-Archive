---
title: "setting ip via gui umbuntu"
date: 2009-11-20
forum: General Help
---

### Post by ulao on 2009-11-20
First I want to state that my main goal, besides simply using umbuntu, is to make it replace the over charged os's like m$. I'm in no way against m$, but I do hold a dark opinion of there merchandising methods. 

That being said. I dont need help putting an ip in Ubuntu. I have no trouble doing it be simply adding and editing the files to make that possible. I wish to make it work out of the box so to speak and trouble free. So.. here is what I did..

>Installed Ubuntu 9.10 
>whent in to system->preferences->network connections. Clicked edit on eth0 ( my lan card ) and put in my info as follows.

using ipv4
set to manual 
192.168.0.23 my ip
255.255.255.0 /sub net
192.168.0.19 my gate way
and I also added the dns..

Now I know this ip combo is good as I use it just fine on my network. But that hardly the issue..

one I do this, I would "assume" the gui would run a restart o the network. If I do a ifconfig its still set to dhcp. If I do a networking restart there i s no change, if I restart the system there is no change. If I go back and check the data in "networking connection" it shows what I put it.

So questions.
1) why does changing the "auto eth0" not reflect the info from ifconfig "eth0"
2) why does it not work?
3) if there is a better way to do this in the GUI I';d be happy to try it.

Again, this is not a question for how to set ip info in a debian system. My unbuntu server has been running solid as a rock from day one. I LOVE IT! this is a thread to empower umbuntu to be the best os out there... Well at least a damn good alternative... Thus, simple things like a GUI network setting  window, should work.

---

### Post by Darce on 2009-11-20
Sorry, gotta ask a dumb question, as I've tried what you described and it works fine for me on 9.10, but are you connected with a wired or wireless connection ? Depending on where I am, I connect with either wired, wireless, or mobile broadband, and can find myself easily getting confued.

Tim

---

### Post by ulao on 2009-11-20
hmm, no, no wireless set up here string cat5. How would this make thing confusing, I'm confused about that now LOL :)

---

### Post by doas777 on 2009-11-20
there used to be a bug that manifested that way. may have come back. you aren't using intrepid, are you?

try deleting 'auto eth0' in network manager, and create a new entity, using eth0's mac, and then applying your ip specs. 
then reboot, and run ifconfig.

---

### Post by ulao on 2009-11-20
isn't intrepid 8 something ? I'm on 9.10.


I never though to compare mac addresses... But deleted it to soon.. I created a new using the mac found in ifconfig and rebooted. The eth0 i added in network connections shows last used never. and the eth0 was not brought up. Could there have been an error, i forget the log that would show that?

Darce, I now see what you mean, there is no way to know the difference, haha good one. no I have it right, but this is a bit confusing I will admit.

---

### Post by doas777 on 2009-11-20
> **ulao said:**
> isn't intrepid 8 something ? I'm on 9.10.


I never though to compare mac addresses... But deleted it to soon.. I created a new using the mac found in ifconfig and rebooted. The eth0 i added in network connections shows last used never. and the eth0 was not brought up. Could there have been an error, i forget the log that would show that?

hmmm. the "never" always shows up for me even while I am connected so don't worry too much about that. it is worrisome however that the interface did not come up. most of your error messages are going to be in /var/log/messages but boot messages usually appear in dmesg or xorg.0.log.

---

### Post by ulao on 2009-11-20
I also tried setting the mtu , instead of automatic.

I look in the log for my ip adress and found no hits. Cant paste in here as I have no net connection..

but as said this is only to help the community, I could always put everything in manually. 

Any other idea before i give up on it?

Not sure if there is a method for this, or if it even gets looked at, but tips to dev..

1) Put a search in the mac address box, so a use can just select it from a list.
2) [not related] I think default monitor would be better at 60 htz not 75, could just be my monitor was old.

---

### Post by Giblet5 on 2009-11-20
The network-manager gui is broken. Who decided that a spreadsheet-cells-in-a-listbox tardwidget was even CLOSE to UI standards-compliant? If you can't navigate a properties page via the keyboard, the interface is 100% broken.

Install wicd. It will remove network-manager. It works very well for DHCP or static configs, it has a usable interface, it does more, it looks better, it's much easier to use, and it has a smaller footprint.

---

### Post by ulao on 2009-11-20
> The network-manager gui is broken. Who decided that a spreadsheet-cells-in-a-listbox tardwidget was even CLOSE to UI standards-compliant?
 - Oh man do we agree there....

> Install wicd. It will remove network-manager. It works very well for DHCP or static configs, it has a usable interface, it does more, it looks better, it's much easier to use, and it has a smaller footprint. I will just add the ip info and try to apt get it.


--update--
Yes this gui worked. much better but painful slow on my system. Seem like its doing interrupts and freezing my system ever second. But it does work. umbuntu should be using this interface. But I guess this is more of a gnome issue? We need a U-shell..

thx for the help. Still not satisfied with either shells for the basic user ( out of box ).

---

### Post by Giblet5 on 2009-11-20
Glit....chy ... be...havior is not normal on Ubuntu.

You can open a terminal window and run ```
top
```

Ctrl+C to stop the continuous updating...

What's using all the resources?

I like keeping tabs on CPU, network and disk, so I right-click my panel (the bar at the top) and add a System Monitor applet. I turn on CPU, network, and disk I/O gauges. It's helpful. To me at least.

---

### Post by ulao on 2009-11-20
I just tried to exit the gui and see I have a out of memory: kill process 1222 gnome session scroe 62843 ir a child killed process 1361 (metacity)

---

### Post by Giblet5 on 2009-11-20
Did you set up a swap partition when you installed Ubuntu.

The ```
free
``` command will tell you how much swap you have.

Not having a swap partition will definitely cause this kind of behavior.

If you have no swap partition, you can create one with gparted (another package to download...sorry)

---

### Post by ulao on 2009-11-20
> **Giblet5 said:**
> Did you set up a swap partition when you installed Ubuntu.

The ```
free
``` command will tell you how much swap you have.

Not having a swap partition will definitely cause this kind of behavior.

If you have no swap partition, you can create one with gparted (another package to download...sorry)

I did not get the option, I will try this if I can remove the problem so that I can use the os ;)

---

