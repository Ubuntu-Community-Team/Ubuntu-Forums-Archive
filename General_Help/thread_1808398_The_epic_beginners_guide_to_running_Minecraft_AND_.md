---
title: "The epic beginners guide to running Minecraft AND Bukkit on Ubuntu"
date: 2011-07-20
forum: General Help
---

### Post by nrock2256 on 2011-07-20
Hello. I am a fairly recent ubuntu user (15 hours as of this poast :D) but i needed minecraft and bukkit running on ubuntu, or it was back to windows! So, here is a guide to running both on Ubuntu!

Minecraft: 

Step 1: Download a Java Runtime Environment (JRE) for ubuntu. 

This is an easy one. Open up the terminal by going to applications>terminal. Then type the following code:```
sudo apt-get install openjdk-6-jre
``` You will be prompted for your password (when you type it it does NOT show any sort of characters) and ubuntu will download and install your JRE. Leave the terminal window open until it finishes.

Step 2: Download the minecraft.jar

go to [http://www.minecraft.net]("http://www.minecraft.net") and click on the download link for beta. Select the minecraft.jar from the linux/other section and download it. Make sure you place it in your /home/USERNAME Folder, where USERNAME is your account name. Ie. My username is noah so my folder path would be /home/noah. (if your not sure what your username is, look near the area where the time is)

Step 2.3: executable bit?

Go to your /home/username folder and find the minecraft.jar you just downloaded. Right click on it, and select properties. Now go to the "Permissions" tab, and click on "allow executing file as program" and hit close.

Step 2.5: Open with JRE, not the archiver.

 Now that the minecraft.jar is executable, Right click it and select "Open with other application". Scroll down and find "OpenJDK Java Runtime 6" and make sure to have it always open with OpenJDK. Hit open, and exit out of the launcher. Your not done.

Step 3.0: Script it up!

Right-click on your desktop and select "Create Launcher..."

Type: Application
Name: Minecraft
Command: java -jar /home/USERNAME/minecraft.jar
Comment: This is optional... You can write whatever you want here.

Hit okay, and it will appear on your desktop.

(Optional)Step 3.5: Download a Picture

Using your favorite image search engine, download a picture to use for the launcher picture. This is the official minecraft launcher picture (the one you would see on windows or osX)  [http://tinyurl.com/3ge6ott]("http://tinyurl.com/3ge6ott") To apply it to your launcher right click on it and select properties. You will see the icon in the upper left of the menu that appears. Click on that. Now find the photo, doubleclick it and hit OK.

Step 4: Start it up!

Just double click on your launcher! it should start up minecraft like normal!


Bukkit

Okay, so bukkit was a tougher nut to crack, but i got it, and i'm 14. (remember that im only making this because it was damn near impossible to find a guide for the basic user)

Step 1: Download craftbukkit. Go to [http://bukkit.org/](http://bukkit.org/) and hit "Get craftbukkit" near the upper right hand corner. on the wiki find the navigation section and select "Main Page" there you will find some colored boxes. Go to the red one and download the recommended build. 

NOTE: If you are coming from windows like me, and already had a server, all you need to do is copy the server folder to your desktop on linux. just make sure you don't try to use the old .bat used to launch it.

Step 2: Scripts!

Before i go on, please note that currently there is no way to make a shortcut to launch the server. if you plan to tuck the server folder away somewhere out of sight and use a link, or write a launcher, you will realize why. Just keep your server folder on your desktop.

That being said, it is quite simple to make a script to launch craftbukkit. First however, rename your craftbukkit from its wierd "craftbukkit-SNAPSHOT blah blah blah.jar" to craftbukkit.jar for simplicity.

Now you need to create a new file. Right click>create document>new file. name it start.sh. Now double click on it and type ```
java -Xmx1G -Xms1G -jar craftbukkit.jar
```    remember that this is the EXACT SCRIPT. do not add anything else. just this one line of code. i recommend copy paste. Also note that you need to put the start.sh file in your server folder.

Step 3: Follow Minecraft Step 3, except for the start.sh.

Note: If the terminal is complaining about too little RAM, just change the numbers in the -Xmx and -Xms of the script. 1G is one gig of ram, 1538M is 1.5 Gigs of ram. just don't exceed your physical ram, and only use up to 75% of your total ram. I run my server at 1538M because i only have 2 gigs of ram, but a lot of people can do more. To see how much ram you have, go to Applications>system monitor and click on the far left tab.



That about sums it up. If you have any questions, feel free to ask me.

---

### Post by DeadlySin9 on 2011-07-20
Hello, nrock2256's friend here to expand on the guide. _It is possible to create a launcher, but you must edit the script to do so_. It only involves one extra line, just add the following:
```
cd /home/USERNAME/Desktop/server
```If you put your server in a different directory, then edit it to match. You script should now look something like 
```
cd /home/USERNAME/Desktop/server
java -Xmx1G -Xms1G -jar craftbukkit.jar
```Now, right click your desktop and click "Create Launcher"
Type: Application In Terminal
Name it whatever you like
For the command, click browse and navigate to your server script (start.sh)
Comment, again, is optional.
Set an icon if you wish, click OK, and you have a launcher!
[U]You may move the server and launcher wherever you like, just make sure to change  the script and launcher to match!
[/U] 
**Tips:**
If you have problems with Java and such, you could try the sun-java6-jre instead, there is a link to open the package in Ubuntu Software Center [B][HERE]("https://help.ubuntu.com/community/Java")

[/B]If you really want to, you can take the .sh off the end of your start.sh script and it will still run as long as it is executable, just change the launcher to match.

If you want your server and Minecraft launcher to show up in your applications (Unity Dock/Launcher whatever its called), move your launcher to /home/USERNAME/.local/share/applications . If the folder does not show up, press CTRL+H while in your /home/USERNAME folder

---

