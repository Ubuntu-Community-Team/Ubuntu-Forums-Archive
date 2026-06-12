---
title: "Toshiba A60 Notebook Server"
date: 2010-07-09
forum: General Help
---

### Post by Mylaa on 2010-07-09
Hello, 

I have an old notebook computer the specs are as follow. 
Intel Celeron 2.8Ghz 
1.5GB RAM
40 GB HDD
1TB External USB HDD 

The computer will constantly be running in my cupboard 24/7. Using it for movies, videos and pictures. Just a home file server so I can I backup all my digital items. 

What version of Ubuntu should I be using? Server or Desktop? Right now I'm using Windows XP Professional at the moment but I'd rather use Ubuntu personally. 

Thank you! :o

---

### Post by mörgæs on 2010-07-09
Hi, welcome to the forum. 

You can just begin with a desktop version and then add server components as needed later.

---

### Post by Mylaa on 2010-07-10
Thank you so much, that's what I'll start using first.

---

### Post by mörgæs on 2010-07-11
You are welcome. 
When the machine is running, you probably want to take a look at Samba.

---

### Post by Mylaa on 2010-07-12
> **mörgæs said:**
> You are welcome. 
When the machine is running, you probably want to take a look at Samba.

Yeah, I accidentally went ahead of myself and installed Ubuntu Server Edition and got extremely confused with the process but Google said Samba was the best route to take, regardless I couldn't get it to work for the life of me so I'm downloading the desktop version suggested earlier. 

I was going to hire a local tech to come setup my server be he charges 20 dollars an hour, figure I'm better off using the versions and suggestions from the professionals here :o

Again thank you for all the assistance!

---

### Post by Zelandeth on 2010-07-12
If you're new to things, starting with a Desktop version is probably the sensible route - that's what I did with the old Duron 1200 which runs as my web server.  It's a creaky slow old machine, but for what I ask of it, it does the job.

Having the GUI there just makes things a bit easier if things do go wrong or when you're first setting things up.

Just make sure with the A60 that you ensure it's well enough ventilated (maybe run it upside down?) as these laptops apparently had a bit of a reputation for overheating issues which could cause stability problems.  Don't imagine running as a server would be too CPU intensive though as to generate a massive amount of heat.

---

### Post by Mylaa on 2010-07-12
> **Zelandeth said:**
> If you're new to things, starting with a Desktop version is probably the sensible route - that's what I did with the old Duron 1200 which runs as my web server.  It's a creaky slow old machine, but for what I ask of it, it does the job.

Having the GUI there just makes things a bit easier if things do go wrong or when you're first setting things up.

Just make sure with the A60 that you ensure it's well enough ventilated (maybe run it upside down?) as these laptops apparently had a bit of a reputation for overheating issues which could cause stability problems.  Don't imagine running as a server would be too CPU intensive though as to generate a massive amount of heat.

Yeah that's what I've heard too. This is the Toshiba A60-JL1 (Canadian version.) The previous owner before it was given to me said he replaced the cooling fan inside the notebook and modified the DC connector with solder and a much stronger pin connector. I've always got it mounted on top of a USB cooler so hopefully overheating won't be an issue. 

Also my last question (which I haven't tested yet) will a USB 1.0 work correctly with a 1TB external HDD? Such as streaming HD movies across the USB 1.0 interface (plugged into the notebook) and then over Ethernet? I don't see this being a problem but I also want to know if the operating system will detect 1TB too. 

Thanks!

---

### Post by mörgæs on 2010-07-12
Before you hire someone, take a look at this:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Samba_File_Sharing](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Samba_File_Sharing)
It is not a long process to set up.

If heat is a problem, as Zelandeth mentions, you could add an applet to the top panel which controls the CPU clock frequency. Right-click on the top panel and choose 'add', then you will see the applet.

---

### Post by mörgæs on 2010-07-12
> **Mylaa said:**
> 

Also my last question (which I haven't tested yet) will a USB 1.0 work correctly with a 1TB external HDD? Such as streaming HD movies across the USB 1.0 interface (plugged into the notebook) and then over Ethernet? I don't see this being a problem but I also want to know if the operating system will detect 1TB too. 



Ubuntu will handle 1 TB, that is for sure, but I guess that the bandwidth in USB 1 is too narrow for streaming. I don't know for sure, though.

---

