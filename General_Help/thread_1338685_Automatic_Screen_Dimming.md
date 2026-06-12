---
title: "Automatic Screen Dimming?"
date: 2009-11-26
forum: General Help
---

### Post by Happyman7 on 2009-11-26
Hi

  I was wondering if I there is an application or some kind of do-hickey that *automatically* dims the screen at a certain time of day and then brightens it up at another time.
  I was wondering because I hate, after getting really comfortable and in a "work mood", that I have to get up and turn off/on the lights so my eyes don't hurt. Or if I am on the laptop, it is just awkward to adjust it. 

*If you still don't understand:*
Here's a scenario:
I get on the computer midday (12:15 pm) and have a project that will take a long time to do. It starts getting dark at around 5 o'clock PM, so I have to get up and adjust the lighting or whatever to compensate for the light change. So at midday, the brightness would be around 95% and when 5 o'clock came around, it would dim the screen to 45%.

(The scenario is not real)

```
Machine Information:
Laptop
-Acer Aspire 5735Z
-Running Windows Vista Home Premium (which is closely related to cow manure) and Ubuntu 9.10/Karmic Koala
--Ubuntu is installed inside Windows
-2x Intel Pentium Dual CPU T3200 @2.00GHz
-Screen Resolution of 1366x768
-Memory of 1990 MB
Desktop
-Dell XPS 410
-2GB RAM
-+100 GB of Hard drive Space (I'm not on it, so I don't exactly know)
-LCD Screen w/ resolution AROUND 1600x1020
-Running Windows XP SP2/SP3 (not sure) and Ubuntu 9.10/Karmic Koala
--Ubuntu is installed within Windows
```I hope that someone is able to help or lead me to a link that does what I want.:)

---

### Post by VCoolio on 2009-11-26
There is [f.lux]("http://www.stereopsis.com/flux/"), the linux version is called [xflux]("https://secure.herf.org/flux/xflux.tgz"). Extract and put the file anywhere you like, preferably somewhere in your $PATH, then run it with your latitude like this:
xflux -l 52.0

---

### Post by Happyman7 on 2009-11-27
I'm sorry but I don't really understand *all* the ubuntu/Linux lingo;
What do you mean by "$PATH" and "latitude"? And do I run that in terminal?

---

### Post by raktarok on 2009-11-27
Latitude is probably the 'normal' latitude. You would need that for a program like this right? When it 12:15 in your place, it may not be the same time in another latitude :)

Do **echo $PATH** from a terminal,and you will have an idea what it is.
Mine currently gives this:
```
/home/anup/bin:/home/anup/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
When you type a something in a terminal, these are the directories that get searched to see if what you typed is a command of some sort. This is not an exact description, but the end result is that if you put the main program file you downloaded in one of these places, you can run it from any other directory(while in terminal) or launchers,menus, etc by *using the program name only*. 
In short, just put what you downloaded(after extracting the archive, of course) in /usr/bin/ (or any other folder in the list). then you can issue the above command from any directory or you can create a launcher for it by just using its name. 

But if you don't copy it in one of those directories, then you will have to specify the full path when you add it to your startup applications list.(eg if its in your home folder, specify /home/your_user_name_/xflux -l 52.0) 

I hope you understood - I did not explain this properly, I think. 

Actually, there is another way to do what you want, by using cron and some commands to change the brightness. If you are not satisfied with the program above, post again. I will try to help.

---

### Post by VCoolio on 2009-11-27
Thanks for clearing it up for me, my latitude will have told you I was asleep ;). Actually at least I am interested in the commands to change brightness; xflux changes just two times: at sunset it fades within 15 seconds, at dawn it brightens up in 15 secs, so no stretched period or gradual change. But it may be difficult to set up brightness correctly ourselves, regarding colors and stuff.

---

### Post by John Bean on 2009-11-27
> **Happyman7 said:**
> Or if I am on the laptop, it is just awkward to adjust it. 

I'm lazy too, but not that lazy ;-)

Or is it that your laptop have hotkeys to adjust brightness? They work on every laptop I've used in recent times but without them I can imagine it's a bit of a pain to adjust.

---

### Post by raktarok on 2009-11-27
@VCoolio,
In my laptop at least, I can change the brightness to a moderate level with this command, but the command may not be exactly same for other laptops with different chipsets. 
```
sudo echo 7 > /sys/devices/virtual/backlight/acpi_video0/brightness
``` 
Check if the directory acpi_video0 exists, and even if it does not exist, there should be a directory there with files like brightness and max_brightness. Just replace the directory in the command with the one in your system, and it should work.

Doing **cat /sys/devices/virtual/backlight/acpi_video0/max_brightness** gives the value 15 in my laptop. So in the above command, I can put any number from 0 to 15. 0 would give the least brightness and 15 the maximum. 

@happyman7 
you can put these lines in the file /etc/crontab.(Of course, you need to check if the directory in the above commands is valid in your laptop, and also check the maximum brightness level as described above. The first line that starts with # is a comment, you don't need to add that)
```
#At 12:15 pm, increase the brightness and at 5:00 pm, decrease it. 
15 12 * * * root echo 14 > /sys/devices/virtual/backlight/acpi_video0/brightness
0 17 * * * root echo 7 > /sys/devices/virtual/backlight/acpi_video0/brightness 
```
The file crontab is there to schedule repetitive system tasks. The first two numbers(15,12 and 0,17) give minute and hour respectively and thus, you can specify any time of the day. You can even specify day of month, month and day of week. These are represented by * here, meaning include all months and days. The 'root' after this indicates that the command is to be run as superuser. You can use other usernames, but the use of root here eliminates the need of 'sudo' in the brightness changing command. And this is very handy, we don't need to enter password to change the brightness. 
If you don't like editing /etc/crontab by hand, you can install **gnome-schedule**, a graphical frontend to cron.    

and happyman7, are you really that lazy? :) 
or is it that you don't have brightness hotkeys in your laptop? If so, a small script can be written to change brightness with some keys.

---

### Post by Happyman7 on 2009-11-29
Thanks! I'll get round to checking it out!

---

