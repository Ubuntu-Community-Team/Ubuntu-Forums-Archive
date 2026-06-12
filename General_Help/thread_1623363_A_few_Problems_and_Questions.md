---
title: "A few Problems and Questions"
date: 2010-11-16
forum: General Help
---

### Post by timfinley on 2010-11-16
First I have Ubuntu 10.10 installed on my compaq presario v6000, fedora 14 on my hp pavilion zv6000. On my Fedora box I have my Brother MFC240c printer up and running. 

I want to share printing over the network. Send print jobs to the Fedora box.... Can't seem to figure that one out.

 I also have Ubuntu 10.10 installed on a desktop. I want to share folders and files, but i keep running into authentication problems. 

Another question I have is about broadcasting music (video if possible) like radio throughout my home network. 

Other PC's in my home are two Windows 7 boxes and an Xbox360. While streaming media to these other devices would be cool, its not a priority. I already have ushare for videos to my Xbox. 

Printing and File Sharing are the biggest priority. Any help would be appreciated.

---

### Post by cariboo on 2010-11-16
Go into the cups administration console on the system running Fedora, and make sure the printer is set to be shared, open your browser and type:

```
http://localhost:631
```

click the administration tab, and select the checkbox beside  **Share printers connected to this system**, then click the change settings button. You will be asked for you root password.

Then go to your Ubuntu system and select System->Administration->Printing, and click add printer,  click Network Printer, highlight Internet Printing Protocol, and enter the ip address of your Fedora system, then click forward. The rest of the setup is just the same as setting up a printer connected to your desktop.

---

### Post by timfinley on 2010-11-17
That was very helpful. Same similar process for Windows I imagine? 

Now how can I solve some of the issues with file sharing? 

Is Broadcasting music like a radio station possible? I have seen a few posts about this subject but I have never seen a good reply....

---

