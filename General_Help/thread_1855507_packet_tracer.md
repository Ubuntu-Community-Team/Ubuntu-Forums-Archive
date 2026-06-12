---
title: "packet tracer"
date: 2011-10-06
forum: General Help
---

### Post by samh25 on 2011-10-06
hi guy, any one now how to install packet tracer on 11.04. been trying to install in bin format but its not having any of it

---

### Post by collisionystm on 2011-10-06
Like wireshark?

---

### Post by haqking on 2011-10-06
> **samh25 said:**
> hi guy, any one now how to install packet tracer on 11.04. been trying to install in bin format but its not having any of it

do you mean the cisco simulation package or a packet tracer program.

a good simulation for studying Cisco is GNS3 which is in the repos, if you want a packet tracer program then then Wireshark is in the repos

---

### Post by JSchultheis on 2011-10-11
What about Packet Tracer? As in [[COLOR="Blue"]***_Cisco Packet Tracer 5.3_***[/COLOR]]("http://www.cisco.com/web/learning/netacad/course_catalog/PacketTracer.html").;)

Anybody got some ideas on installing specifically that?;)


Turns out, I have obligations that bind me to do things that way and don't allow for the other options.;)

---

### Post by uRock on 2011-10-11
Move the .bin file to your Home folder, then enter the commands shown on the Cisco.netacad.net site into the terminal,```
chmod +x PacketTracer*.bin
```to make the .bin executable, then enter the follwing to execute the PacketTracer installer.```
./PacketTracer*.bin
```

I would also +1 installing the GNS3 software, which is in the Ubuntu Software Center. The only downfall is getting legal copies of the Cisco IOS images to install within the application.

---

### Post by JSchultheis on 2011-10-11
> **uRock said:**
> Move the .bin file to your Home folder, then enter the commands shown on the Cisco.netacad.net site into the terminal,```
chmod +x PacketTracer*.bin
```to make the .bin executable, then enter the follwing to execute the PacketTracer installer.```
./PacketTracer*.bin
```

I would also +1 installing the GNS3 software, which is in the Ubuntu Software Center. The only downfall is getting legal copies of the Cisco IOS images to install within the application.

no uRock!
no, uRock... noooooo, uRock. :p

Well I figured more replies were just going to be solely impositions of what the conjectors assume is best... so I continued researching until I have installed and booted up the actual program desired: Packet Tracer.

I love it when people like 'uRock' actually help, be it answering directly or giving direct advise, even though there may be other options. Seven extra beans to uRock!

I personally use Packet Tracer (ON MY PC), as well as gns3, and wireshark and other nonsense, but for the time being, I needed Packet Tracer, and searched this thread because that was the title. All of the non-PacketTracer info wasted my time and left me wanting to start another thread... think of that...


--------[/vent]

click link for file:

[[COLOR="Blue"][SIZE="2"][FONT="Times New Roman"]***_Packet Tracer bin link_***[/FONT][/SIZE][/COLOR]]("http://195.148.217.80/Public/Cisco/Programs/PacketTracer/Linux/Ubuntu/PacketTracer53_i386_installer-deb.bin")

open terminal, I happened to be in the Downloads folder, if that matters:
```
cd Downloads
bash ./PacketTracer53_i386_installer-deb.bin
```

you will be asked to read the EULA. 
press 'enter' about a hundred or so times.
make sure to press 'y' when asked (or 'n' if you don't accept the EULA[?]) hehe
the install should then complete, with the last statements being similar to:```
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...

```

Then go to Menu>Internet>Cisco Packet Tracer
oh yeah, I use Peppermint OS, so you may go to Application>Internet>Cisco Packet Tracer or something like that...

:cool:

it took longer to create this post than it did to install PT hehehe

---

### Post by Kill-Switch-&gt; on 2011-10-11
Vary nice job !! this made installing very EZ .. and i too hate when you ask a question and every one wants to talk about what they think is better for you .. as you know i too use both Packet tracer and Gns3 .. and wanted both to be able to use . This was a helpful thread . keep it up ..

---

### Post by uRock on 2011-10-11
I didn't see anyone saying a tool was better. They are both great tools to have.
Definitely nothing worthy of a rant.

---

### Post by JSchultheis on 2011-10-12
[[COLOR="Blue"][SIZE="2"][FONT="Times New Roman"]***_Click for funky font fixing thread._***[/FONT][/SIZE][/COLOR]]("http://ubuntuforums.org/showthread.php?t=1840443&highlight=packet+tracer")



Also, thanks again, uRock, and glad it worked for you, KillSwitch!

---

### Post by Edaw 0 on 2012-01-17
Thanks uRock! [IMG]http://img.photobucket.com/albums/v505/Edaw010/thumbup.gif[/IMG]

---

