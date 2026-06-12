---
title: "how to display download speed"
date: 2009-12-23
forum: General Help
---

### Post by Tehut on 2009-12-23
Hi,

in Jaunty and earlier versions of Kubuntu, the status window one could open via the system tray (icon was an 'i') for a download included the current speed of download, for example 1000 kb/s.
In Karmic this is missing. Only the source & destination and current/total file size of the download are displayed.
Is there a way to get the current speed of the download back?
Download meaning one started via Konqueror.

If anyone knows how to do this: Thank you very much.

---

### Post by plusnplus on 2009-12-23
i also want to know, but in ubuntu.

---

### Post by iponeverything on 2009-12-23
Right click on the status bar and click on "+ Add to Panel"
Hight light "System Monitor" and click on "Add"

Then click on the System Monitor icon on your status bar and you will be able to see your current download/upload rates.

---

### Post by gs777 on 2009-12-23
There are two fantastic programs for the job, besides "system monitor". One is called " vnstat" which is a command line utility. This can display your traffic speed and can keep record of your data usage on  monthly, yearly daily or hourly basis. I would recommend this program.I myself use this. Install it by typing " sudo apt-get install vnstat" .Enjoy.
  Another program with less features is called "Netspeed". It has a GUI and can display your  network speed bu cannot keep track of your data usage . However it can display the data usage in any particular session. To install this and to know more about it see [this ]("http://www.gnome.org/projects/netspeed/")link.
however from your aptitude I think you will like this utility as well .

---

### Post by iponeverything on 2009-12-23
> **gs777 said:**
> There are two fantastic programs for the job, besides "system monitor". One is called " vnstat" which is a command line utility. This can display your traffic speed and can keep record of your data usage on  monthly, yearly daily or hourly basis. I would recommend this program.I myself use this. Install it by typing " sudo apt-get install vnstat" .Enjoy.
  Another program with less features is called "Netspeed". It has a GUI and can display your  network speed bu cannot keep track of your data usage . However it can display the data usage in any particular session. To install this and to know more about it see [this ]("http://www.gnome.org/projects/netspeed/")link.
however from your aptitude I think you will like this utility as well .

cool on vnstat -- thanks. I am using cacti to track traffic stats, but this will be good to double check the numbers since my cacti has a polling interval of 5 minutes.

---

### Post by iponeverything on 2009-12-28
Have to say vnstat is coolest little utility that I have been turned on to in a while. Here in Dushanbe, almost everyone has pretty low bandwidth cap -- so having vnstat generate summaries of utilization of broken down by hour/day/month is super cool. While Cacti does give some nice pretty pictures, I have to say the way data presented by vnstat much more useful for what I need. So, thank you gs777.

---

### Post by Tehut on 2010-01-19
As far as I can tell, none of those programs are able to display download / upload speed for a specific download. But thank you.
It's been fixed in the meantime.

---

