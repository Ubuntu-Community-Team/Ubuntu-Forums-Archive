---
title: "what is command for &quot;run&quot; in terminal?"
date: 2012-04-28
forum: General Help
---

### Post by gabmuks on 2012-04-28
Hello to all and good day.

I recently tried to add a program via terminal.
I followed all instructions and copied and pasted into terminal.
And after successfully completing everything as instructed,
the last instruction said to open a terminal and run conky.

What is the proper terminal command to "run" something???

Can anyone please help?

---

### Post by PhantomTurtle on 2012-04-28
To run a program, you just type in the name of the program into terminal, such as typing in,
```
nautilus
```
will open the file browser. So try typing in "conky" into terminal.

---

### Post by pbrane on 2012-04-28
If you want to run conky in the foreground leaving the terminal open you can type
```

conky

```

if you want to run conky in the background and close the terminal you should run
```

conky -d

```

basically you just type the name of the program, and any arguments you need in the terminal. You could also try ATL+F2 and type the command.

---

### Post by gabmuks on 2012-04-28
Thank you all for your help.

Conky is now running I guess...

Conky seems to be a just a black screen
with white script.

It is located in the upper left corner of Desktop.

It keeps updating itself with PID, CPU%, MEM%
and other things that I can't read
because the desktop icons are blocking
part of the Conky screen.

How do I turn it off?

Is this all that conky does??

It is not anything like what was described in the information
that I read.

Am I missing some important step??

---

### Post by m_duck on 2012-04-28
That's [Conky](http://conky.sourceforge.net/) in its standard livery by the sounds of it. To "turn it off", if you ran it from a terminal, go back to the terminal and hit ctrl+c. That will kill most stuff that you don't want in the terminal. Depending on how Conky was launched, it may still be running after that, but that can be rectified by typing the following in a terminal:```
killall conky
```

Conky can do a large amount, from just being a system monitor to telling you the news and weather (as well as a plethora of other things - check the link in my sig). Configuring it can seem like a daunting task the first few times though!

---

### Post by gabmuks on 2012-04-28
Bad news...

Now I can't use terminal anymore.
Terminal comes up without a cursor...

Maybe I better give up trying new stuff
before I lose my browser and email
or my mind completely


Thanks for all your help

I just seen your reply "3.1416" but conky has high-jacked my computer.
I can't enter anything into a terminal.
Can you help?

---

### Post by gabmuks on 2012-04-28
I just seen your reply "3.1416" but conky has high-jacked my computer.
I can't enter anything into a terminal.
Can you help?

There must be someway to get terminal back....

---

### Post by m_duck on 2012-04-28
Could you post a screenshot (press the Print Screen button and a capture window should come up)? How do you mean without a cursor? 

You should be able to open a second terminal window or tab - try *File - Open Terminal* when the current terminal is selected.

Please correct me if I've misunderstood.

---

### Post by gabmuks on 2012-04-28
This is what conky is running (I think)
Is there something on here that I can change
that will help?




# Conky settings #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
#imlib_cache_size 0

temperature_unit fahrenheit

# Window specifications #

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 200 250
maximum_width 200

alignment tr
gap_x 35
gap_y 55

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5

uppercase no

temperature_unit celsius


default_color FFFFFF

# Lua Load  #
lua_load ~/.conky/clock_rings.lua
lua_draw_hook_pre clock_rings

TEXT
${voffset 8}${color FF6600}${font caviar dreams:size=16}${time %A}${font}${voffset -8}${alignr 50}${color FFFFFF}${font caviar dreams:size=38}${time %e}${font}
${color FFFFFF}${voffset -30}${color FFFFFF}${font caviar dreams:size=18}${time %b}${font}${voffset -3} ${color FFFFFF}${font caviar dreams:size=20}${time %Y}${font}${color FF6600}${hr}
${voffset 140}${font caviar dreams:size=10}${alignr}HOME${font}
${font caviar dreams:size=12}${color FFFFFF}${alignr}${weather [http://weather.noaa.gov/pub/data/observations/metar/stations/](http://weather.noaa.gov/pub/data/observations/metar/stations/) LQBK temperature temperature 30} °C${font}
${image ~/.conky/new-ubuntu-logo.png -p 64,125 -s 70x20}

${color FFFFFF}${goto 25}${voffset 35}${cpu cpu0}%
${color FF6600}${goto 25}CPU
${color FFFFFF}${goto 50}${voffset 23}${memperc}%
${color FF6600}${goto 50}RAM
${color FFFFFF}${goto 75}${voffset 23}${swapperc}%
${color FF6600}${goto 75}Swap
${color FFFFFF}${goto 100}${voffset 23}${fs_used_perc /}%
${color FF6600}${goto 100}Disk
${color FFFFFF}${goto 125}${voffset 25}${downspeed eth0}
${color FFFFFF}${goto 125}${upspeed eth0}
${color FF6600}${goto 125}Net



${color FFFFFF}${font caviar dreams:size=8}Uptime: ${uptime_short}
${color FFFFFF}${font caviar dreams:size=8}Processes: ${processes}
${color FFFFFF}${font caviar dreams:size=8}Running: ${running_processes}


${color FF6600}${font caviar dreams:size=8}${alignr}${nodename}
${color FF6600}${font caviar dreams:size=8}${alignr}${pre_exec cat /etc/issue.net}  $machine
${color FF6600}${font caviar dreams:size=8}${alignr}Kernel: ${kernel}

---

### Post by gabmuks on 2012-04-28
I will try....



I took the screen shot..but how do I place it in this reply??

---

### Post by gabmuks on 2012-04-28
Will this work?
I don't know....

[http://file:///home/liz/Pictures/Screenshot%20from%202012-04-28%2016:34:22.png]("http://file:///home/liz/Pictures/Screenshot%20from%202012-04-28%2016:34:22.png")


No that does not work....

---

### Post by m_duck on 2012-04-28
> **gabmuks said:**
> I took the screen shot..but how do I place it in this reply??
[Clicky for attachment process](http://ubuntuforums.org/showthread.php?t=1626753).

---

### Post by gabmuks on 2012-04-28
Did this work?
I hope so....



[ATTACH]216793[/ATTACH]

---

### Post by m_duck on 2012-04-28
Have you logged out / in, or rebooted since this started happening? That might fix things if a config has gone funky somewhere. If that is the normal GNOME terminal, can you try running xterm to see if that does the same or not? Just hit the super (windows) key and type ***xterm***. Getting the terminal working again should be the first task I think.

---

### Post by gabmuks on 2012-04-28
Yessssss!!!!!!


xterm did the trick!!!

This is starting to be fun again!

Thanks so much 3.14!

Any more suggestions?

---

### Post by m_duck on 2012-04-28
It's odd that the gnome-terminal no longer seems to display anything though. My suspicion, since xterm works, is that the font colour in gnome-terminal has been set to the same as the background colour, though I've no idea why that would be...

With respect to the Conky config, I will give helping a go, but I've never used the Lua stuff in it before. Can you run Conky again and post a screenshot of what you get, as well as any output in the terminal it gives?

EDIT: Also, no problem!

---

### Post by gabmuks on 2012-04-28
Here is screen shot 3.14.....


[ATTACH]216794[/ATTACH]

---

### Post by gabmuks on 2012-04-28
You were right again!!!

It was the font color for the terminal.

It was set to black.

Terminal is correct now.

But how could that have been changed?

Seems quite odd..

---

### Post by m_duck on 2012-04-28
OK, that's Conky in its default form so it's not reading the config you posted earlier. You will need to name that config to ***.conkyrc*** and put it in your home directory, so the full path would be:```
/home/gabmuks/.conkyrc
```Alternatively, you can run Conky with an argument telling it where the config is, so if you config was in ***~/Documents/Conky/my_config***, you would launch Conky as:```
conky -c ~/Documents/Conky/my_config
```(NOTE: ***~/** *is just a short way of writing /home/yourusername.)

Once you've done  that, post the output the  terminal spits out after running Conky and we'll see what else needs doing.

RE: terminal - I've not the foggiest... I know the font colour can be set temporarily in a script but not sure about permanently in settings. It might be that, if you have previously set the background to black, and then changed the desktop theme, it could have changed the default colourset itself, without touching the background, resulting in the black on black. But that's just a guess.

*[I'm signing off for a while now, but will be back to help tomorrow if no one else has.]*

---

### Post by gabmuks on 2012-04-28
3.14....can someone change things on my computer
through the Internet?

I remember a few months back, i was having
some problems with Kubuntu.
I got onto launchpad forum.
People started emailing me, saying they could help
if I would give them some sort of permission
to connect with my computer somehow,
which I did allow.
Does that mean these people still have access to my computer?

---

### Post by gabmuks on 2012-04-28
Good Morning 3.1416.
And good day to you!
Here is latest Conky update.
It works now... but I still might need some suggestions.
Here is screen shot.......[ATTACH]216799[/ATTACH]

---

### Post by stinkeye on 2012-04-29
> **gabmuks said:**
> Good Morning 3.1416.
And good day to you!
Here is latest Conky update.
It works now... but I still might need some suggestions.
Here is screen shot.......[ATTACH]216799[/ATTACH]
Hi gabmuks,
Run your conky in the terminal as stated by m_duck.
eg 
```
conky -c [COLOR="Red"]/path/to/your/config[/COLOR]
```
and look for errors.

This section of your config is calling a lua script.
> # Lua Load #
 lua_load [COLOR="Magenta"]~/.conky/clock_rings.lua[/COLOR]
 lua_draw_hook_pre clock_rings
Check you have the script and the [COLOR="magenta"]path[/COLOR] is correct.You can save the lua script anywhere, just adjust the path accordingly.
Check you have the font **[_[COLOR="DarkRed"]caviar dreams[/COLOR]_]("http://www.dafont.com/caviar-dreams.font")**.<---Link.
Check what network interface you are using.The script is using eth0.

For the current temp go here 
[**_[COLOR="DarkRed"]http://weather.noaa.gov/[/COLOR]_**]("http://weather.noaa.gov/")
and search for your location and get the 4 character code from the address.
eg: Mine is [http://weather.noaa.gov/weather/current/](http://weather.noaa.gov/weather/current/)[COLOR="Red"]YPPH[/COLOR].html

Find this section in your config 
```
${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ [COLOR="DarkOrange"]LQBK[/COLOR] temperature temperature 30} °C${font}
```
and insert [COLOR="darkorange"]your location code[/COLOR].
eg my config now reads
```
${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ [COLOR="DarkOrange"]YPPH[/COLOR] temperature temperature 30} °C${font}
```

The config is also loading an image with
```
${image ~/.conky/new-ubuntu-logo.png -p 64,125 -s 70x20}
```
Check you have that image and the path is correct.

Is this the config you are using?
[**_[COLOR="DarkRed"]Conky lua[/COLOR]_**]("http://gnome-look.org/content/show.php/Conky+lua?content=139024")

When configured properly your conky should look like the attached pic.

---

### Post by gabmuks on 2012-04-29
Perhaps you could help me understand something....

In the process of downloading and installing conky,

I was asked to extract and rename and

move certain files to Home folder.

I followed the instructions best I could.

The problem is after moving a file or folder to the "Home" folder,

it simply disappears never to be seen again.

I search all the files I see in the Ubuntu files icon,

But they are not there. They have been hidden somehow.

Is this a security thing? How can I view these hidden files?

I can no longer find "my config" to be able to modify it.

I used to be able to click on .conky and then open it with text editor.

What's the secret?

Thank you for your time

---

### Post by gabmuks on 2012-04-29
> **m_duck said:**
> [QUOTE]OK, that's Conky in its default form so it's not reading the config you posted earlier. You will need to name that config to ***.conkyrc*** and put it in the [COLOR=Red]root [/COLOR]of your home directory,........

That is the problem....why do I not have access to my root directory?
I get a message saying that "I do not have permission".

Wow! I just clicked on the "root" directory and then "Properties"
and then the "Permissions" tab.
It says: "YOU ARE NOT THE OWNER, SO YOU CANNOT CHANGE THESE PERMISSIONS."

So who exactly IS the owner?

---

### Post by oldos2er on 2012-04-29
Poor choice of words? m_duck gave you the correct location ```
/home/gabmuks/.conkyrc
``` meaning your user's home folder, not root's. It's normal not to have write permissions outside of your user's home folder.

---

### Post by stinkeye on 2012-04-29
As to the other problem of not being able to find your files.
Folders and files preceded by a dot are hidden.
When in the file browser press ctrl+h to show hidden.
Most of these hidden files are configs/settings for the programs you run.

---

### Post by gabmuks on 2012-04-29
> **stinkeye said:**
> As to the other problem of not being able to find your files.
Folders and files preceded by a dot are hidden.
When in the file browser press ctrl+h to show hidden.
Most of these hidden files are configs/settings for the programs you run.

Thank you down under....
ctrl+h worked.

But I am not allowed to change anything.
Is that correct?

---

### Post by gabmuks on 2012-04-29
> **oldos2er said:**
> Poor choice of words? m_duck gave you the correct location ```
/home/gabmuks/.conkyrc
``` meaning your user's home folder, not root's. It's normal not to have write permissions outside of your user's home folder.


Thank you Ann

You have helped more that you know.:idea:

---

### Post by stinkeye on 2012-04-29
> **gabmuks said:**
> Thank you down under....
ctrl+h worked.

But I am not allowed to change anything.
Is that correct?

You can edit hidden files in your home folder if you know what you are doing or have been instructed to do so.
As I said most of them are just your saved settings for progams you run and you don't need to do anything with them. 

eg when you run conky it looks for a config @ **~/.conkyrc** to tell it what to display on screen.
The "~" symbol is short for **/home/gabmuks** or in my case **/home/glen**

eg **[COLOR="Red"]~[/COLOR]/.conkyrc** is the same as **[COLOR="red"]/home/gabmuks[/COLOR]/.conkyrc**

So without knowing your username I could tell to run this in the terminal 
to open your conky config in gedit
```
gedit ~/.conkyrc
```

---

### Post by gabmuks on 2012-04-29
> **stinkeye said:**
> 
eg when you run conky it looks for a config @ **~/.conkyrc** to tell it what to display on screen.
  [/CODE]

Thanks DownUnder...That helps.

The problem is I don't even know what the path is to my config file.

I can't physically see the files to know what the correct path is.

The strange part is...when I first started to install Conky, I could see the files.
that I placed in the Home files. 
They were not hidden.
I also was able to click on "root" "Properties" "Permission"
 and give myself permission. Now I am denied access.
It seems to me that someone is able to make changes to my computer
through the Internet. Anytime they feel like it.
Is this true??

---

### Post by gabmuks on 2012-04-30
Here is part of the Conky instructions that I used.
Found on Unixmen.

[ATTACH]216940[/ATTACH]

Finally got conky to work....
M_duck taught me some commands and how to fix my terminal.
I found out how to see my root files from Glen Down Under (ctrl+h)

Then I gave myself permission to add/delete.

Then deleted the extra copies of .conkyrc in root.
(Because I had extracted Tar numerous times... because .conkyrc kept disappearing)

Then, while in the root files, I found my mistake.
I had wrongly named .conkyrc as .conky during one of my attempts.

So I deleted the .conky and left  a single .conkyrc in the root.


Success!!! Conky works Great! I put in my weather location
according to Glen's instructions.
and changed C degrees to F degrees.


I learned alot from this experience
 that I would not have learned
 from Ubuntu Software  Center.

I truly thank you all for your patience and kindness. It does my heart good to see that there are still some people on this planet that want to help each other.
Pat L.

[ATTACH]216941[/ATTACH]

---

### Post by stinkeye on 2012-04-30
> **gabmuks said:**
> Here is part of the Conky instructions that I used.
Found on Unixmen.

[ATTACH]216940[/ATTACH]

Finally got conky to work....
M_duck taught me some commands and how to fix my terminal.
I found out how to see my root files from Glen Down Under (ctrl+h)

Then I gave myself permission to add/delete.

Then deleted the extra copies of .conkyrc in root.
(Because I had extracted Tar numerous times... because .conkyrc kept disappearing)

Then, while in the root files, I found my mistake.
I had wrongly named .conkyrc as .conky during one of my attempts.

So I deleted the .conky and left  a single .conkyrc in the root.


Success!!! Conky works Great! I put in my weather location
according to Glen's instructions.
and changed C degrees to F degrees.


I learned alot from this experience
 that I would not have learned
 from Ubuntu Software  Center.

I truly thank you all for your patience and kindness. It does my heart good to see that there are still some people on this planet that want to help each other.
Pat L.

[ATTACH]216941[/ATTACH]

Congratulations. Blends in well with the desktop. 

Just a note on home, root and permissions.
Open up your file browser and click on **File system** in the left column.
Hit ctrl+l to show the full path.(lower case L)
You will see your in the "/" or root directory. 
You will also see a folder in this directory called root which can be confusing.Think of this root folder as the system admins home folder.
[ATTACH]216952[/ATTACH]

Now click on the home folder and you will see the user accounts.
You may have more than one depending if you have added extra accounts for
other users.
[ATTACH]216953[/ATTACH]

Click on your user name and you are now in your home directory.
These files belong to you and contain your configs/settings which are read when you log in.
You can read and write to these files.
[ATTACH]216954[/ATTACH]

You should have no need to edit files outside of your home directory
unless someone instructs you to, and you shouldn't be changing permissions to files/folders outside your home directory.
This is what makes linux secure.

---

### Post by gabmuks on 2012-04-30
Thank you Glen for your kind reply.

I realize now that I was making assumptions
about "root" which I knew nothing about.
And I have a tendency to jump to conclusions.
I really like Ubuntu and like to learn new things
about it. Again I wish to thank you for your patience.
And thank you for the tricks that you all have shown here
in this thread. Makes it more fun to use Ubuntu.

Pat L.

---

### Post by m_duck on 2012-05-01
I'm glad you got this sorted - sorry I disappeared halfway through. Work happened, and wouldn't stop!

Going back to the remote access that other people had to your machine - do you remember what you did to enable it? If it is always running, it could pose a security risk down the line. If it was just enabled as a one-off and isn't running automatically, all should be well.

---

### Post by gabmuks on 2012-05-01
Thanks for returning m_duck.
I tried searching my email archives for
all the offers to fix my software problem
by allowing access to my PC.
I must have deleted all of them.
Is there any way to find out if someone has access now?
Also, when I clean installed to Ubuntu 12.04,
would that have stopped any outside access by those persons?

On a different subject, I came across a driver update for NVIDIA
(i have NVIDIA graphics) that is supposed to.....

"closed a security vulnerability which made it possible for attackers to  reconfigure GPUs to gain access to arbitrary system memory. Fixed a bug  that caused DisplayPort devices to occasionally fail to turn back on  after the system is resumed from suspend."

My display fails to turn back on after suspend. And PC locks up.

After I install this NIVDIA driver in terminal, at the very end, the install aborts itself
and displays a message about xserver.

The NIVIDIA update is 295.40.

[ATTACH]217035[/ATTACH]

---

### Post by gabmuks on 2012-05-01
Hello again 3.1416!

I googled "how to stop X server and got the command...
sudo service lightdm stop.

So I stopped xserver and the screen went blank except for blinking cursor.
So I started the installation code for NIVIDIA. but nothing happened.
But eventually the usual terminal script appeared
so I re-entered the NVIDIA install commands.

It worked!!

I restarted computer and so far no damage has been done.

---

### Post by JKyleOKC on 2012-05-01
If you did in fact do a full "clean install" of 12.04, that would have wiped out all remote access permissions you had granted anyone previously. You can read the file /var/log/auth.log to see who or what has logged into your system. Be warned that this log can be quite alarming the first time you see it, because it logs EVERY login, and the system logs in to itself quite frequently to do behind-the-scenes housekeeping.

For instance, on my system there's a repetitive entry every hour, at 17 minutes and one second past the hour. It's actually the internal scheduler making its hourly check to see if there's anything that needs to be done. The system does similar checks on a daily basis, and again weekly and monthly. You'll also see reports for each time you use "sudo" to modify something outside of your home directory.

The thing to look for, initially, is a login by some user name that you do NOT recognize. Your own, of course, is okay, and "root" is by far the most prevalent one and is also okay. Others should be suspect.

I hope this helps you become more familiar with the system. It can get quite complex under the hood, but the more you know about what's happening, the safer you will be.

---

### Post by gabmuks on 2012-05-01
I tried a few different ways to enter the file that you suggested.

But nothing seems to work. Sometimes it says "access denied".
I must be doing something wrong. How do I find this log??


[ATTACH]217055[/ATTACH]

---

### Post by JKyleOKC on 2012-05-01
In a terminal window, type "less /var/log/auto.log" (without the quotes) and you should see the first screenful of entries. The Enter key will advance you by one line and the spacebar by a full page. Type "q" to quit the "less" program and get back to the terminal prompt.

It's easier, though, from the GUI window. Unfortunately I'm using an older version so don't know the exact commands to do so. I would start by selecting "File System" and from that display selecting "var" and from the resulting window "log" which would show all of the log files, in alphabetic order. Double clicking on "auth.log" then opens the log itself in the default text editor so you can scroll through it. You would not be able to write to it, but could read it at your leisure.

Hope this helps!

---

### Post by gabmuks on 2012-05-01
Wow...this IS disturbing Mr Kyle.

There are quite a few people logging in...

Apr 30 09:20:47 liz-PC180A-ABA-a635w polkitd(authority=local): [COLOR="Red"]"Unregistered Authentication Agent"[/COLOR] for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.37, object path /org/gnome


Apr 30 10:17:01 liz-PC180A-ABA-a635w CRON[2203]: pam_unix(cron:session): session closed for user root
Apr 30 11:17:01 liz-PC180A-ABA-a635w CRON[2277]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 30 11:17:01 liz-PC180A-ABA-a635w CRON[2277]: pam_unix(cron:session): session closed for user root


This polkitd shows up every few minutes in the log.

Apr 30 15:46:05 liz-PC180A-ABA-a635w polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.35, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)

The CRON [2277] looks okay....
But "polkitd" shows up every few minutes in the log.


Does all this look normal to you Mr Kyle?

---

### Post by m_duck on 2012-05-01
Ah, if you have installed a clean install since, it should all be fine. The above looks normal to me, though I'm far from an expert. Consolekit usually just looks at local stuff as far as I'm aware to manage hardware and bits and bobs. I really don't know about it in detail, but I'd not be worried about that.

Cron will be run as root as, well, it runs as root. Cron is just a background process that runs stuff regularly.

---

### Post by gabmuks on 2012-05-01
Thanks 3.1416 !!

Thanks for watching out for me.

I just installed Ubuntu Tweak 7.0.

Is that good?

It seems to clean out all unused data.

---

### Post by JKyleOKC on 2012-05-02
My apologies for being slow getting back to you, and thanks to m_duck for filling in the gap.

The entries you show look completely normal. The CRON entries have the same minute and second in their time stamps as do those in my own log, at 17:01 past the hour, for the hourly check. The polkitd entries probably result from the password dialogs that show up when you run "gksudo" or "gksu" since those programs access the "policy kit" daemon to check the password you provide.

The main thing to look for, as I said before, are user names that you don't recognize. It's extremely unlikely that you will find any, and the valid entries provide huge amounts of "noise" in which they can hide, which is probably why few of the security tutorials mention this log. However when one has good cause to suspect unauthorized entry -- and you did have -- it can provide the smoking gun, or its absence.

---

### Post by gabmuks on 2012-05-02
Thank you Mr. Kyle

I am very happy to hear your kind reply.

I will use what you have taught me
and occasionally check the log.

This has been very educational thread for me!

The whole world could learn a lesson

about community from this site.

I have.

---

