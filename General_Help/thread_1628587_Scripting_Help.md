---
title: "Scripting Help"
date: 2010-11-22
forum: General Help
---

### Post by hantechbl on 2010-11-22
I'm having troubles with my script it says error line 18 unexpected something But it appears to be with the option mechanism I am using, here Is what i got....
```
#!/bin/bash
#MineOS Server Installer
#v1 Initial layout
#v2 Revised code
#v3 Code base completely redone.
#---------------------
echo MineOS Server Installer v3
echo Initializing
echo I am fetching Minecraft server....
wget http://minecraft.net/download/minecraft_server.jar
echo Fetched Minecraft Server .jar
echo Would you like to install hmod?
           OPTIONS="y/n"
           select opt in $OPTIONS; do
               if [ "$opt" = "y" ]; then
                echo fetching Hey0's server mod....
		wget http://lb543.66ghz.com/downloads/hmod.zip
                echo Installing hMOd....
		unzip hmod.zip
		echo hMod Installed.... 
		echo Configuring....
		su chmod 777 server_nogui.sh 
		echo Would you like me to automatically run the server?
			OPTIONS="y/n"
           			select opt in $OPTIONS; do
               		if [ "$opt" = "Y" ]; then
                		echo I'll start the server with hMod
				sh /home/server/server_nogui.sh
                		exit
               		elif [ "$opt" = "No" ]; then
                		echo run sh /home/server/server_nogui.sh
				echo If server errors come up please run this script again.
				echo Typically the indicator is when the server says something,
				echo about outdated clients.
				exit
               		else	
                		echo bad option
              			 fi
           			done
               elif [ "$opt" = "no" ]; then
                echo Install finished...
		echo Would You like Minecraft Server Executed? <y/n>
			OPTIONS="y/n"
           		select opt in $OPTIONS; do
               		if [ "$opt" = "y" ]; then
                	echo run: java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
			echo If you want to run Minecraft server.
                	java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
			exit
               		elif [ "$opt" = "n" ]; then
                	echo Run: java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
			echo To execute minecraft.
				echo If server errors come up please run this script again.
				echo Typically the indicator is when the server says something,
				echo about outdated clients.
				exit
               		else
                	echo bad option
               		fi
           		done
               else
                echo bad option
               fi
           done
```
can anybody tell me where I am going wrong, and how to correct it?
Update:  Exact Message: 
'/install.sh: line 18: syntax error near unexpected token 'do
'/install.sh: Line 18:               select opt in $OPTIONS; do

---

### Post by t4thfavor on 2010-11-22
Whats this doing? It looks incorrect, other than that, I don't see anything funny.

```

OPTIONS="y/n" Correct syntax? maybe {"Y","N"};?

su chmod 777 server_nogui.sh Run this code, should it be su, sudo, or just chmod?

```

Other than that, consider this a free bump:)

---

### Post by hantechbl on 2010-11-23
This automatically installs Minecraft server, I got the option code from a guide, it works, fetches Minecraft server.jar and it stops at the option code and says syntax error.

---

