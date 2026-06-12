---
title: "Help with a shell script for Network Testing"
date: 2012-04-02
forum: General Help
---

### Post by Alphamonkey on 2012-04-02
Hi, I am fairly new to doing the CLI with linux but I am taking a class on it and we are studying shell scripting. I am also studying for my CCNA so i thought it might be fun to make a shell script to test network connectivity. I have one that works which I will post below but I know it is not a good way to go about it. I was looking for advice on how to make the script better. Specifically concerning the part to ping the default gateway and the part to ping the NIC.

"
```
#!/bin/bash
#
# This is a script to test network connectivity.
# It is an ongoing project.
# My POORLY written script.
#
while :
do
# Sets this script to a loop
clear
#
echo "########################################################################################"
echo " Network Connectivity Tests"
echo "########################################################################################"
echo " Please choose a numeric option"
echo "########################################################################################"
echo "1) ping the loopback interface \
               *Used to test the tcp/ip stack on a local host"
echo "2) ping the local hosts IP address \
               *Test the actuall NIC"
echo "3) Ping the default Gateway \
               *Test your ability to leave your local network"
echo "4) Ping a known good internet site \
               *Will be using www.google.com"
echo "5) Show Netstat -r"
echo "6) Ping a user entered IP address"
echo "7) Exit"
echo "#######################################################################################"
echo "Enter your option: [1 - 7]"
echo "############################################################ ###########################"
read choice_num

case $choice_num in

    1) ping -c 5 127.0.0.1 ; read ;;
    2)my_ip=`ifconfig | grep inet | grep -i bcast | cut -d ':' -f 2 | cut -d ' ' -f1` 
      ping $my_ip ; read ;;
    3) def_gate=`netstat -r | cut -d ' ' -f 10`
       ping -c 5 $def_gate ; read ;;
    4) ping -c 5 [www.google.com](www.google.com) ; read ;;
    5) netstat -r ; read ;;
    6) echo "enter an IP"
      read user_def_IP
      ping -c 5 $user_def_IP ; read ;;
    7)exit 0 ;
esac
done
```
"

Thanks, I would appreciate any feedback. oh and sorry if the code didn't post correctly I am not sure how people post "code"

---

### Post by nothingspecial on 2012-04-03
> **Alphamonkey said:**
>  oh and sorry if the code didn't post correctly I am not sure how people post "code"

Hi, the easiest way to do that is to highlight the text then click the # in the formatting options at the top of the posting box.

---

### Post by Zorael on 2012-04-06
I love tinkering with scripts. :3

Take a look at [this paste](http://paste.ubuntu.com/917338) for some ideas. (To be completely honest I copy-pasted some of the functions I use in other script.)

What approach to use to tackle problems mostly comes down to the programmer's own coding preferences. Obviously there are better and worse solutions, but it's seldom very important in shell scripts where performance isn't a big priority. I like breaking up stuff into functions to keep the actual execution part very small, but for all I know that's bad practice. It's certainly not very script-like.

You may want to get into the habit of defining settings as constants at the top like that. It makes it easier to change them without having to search-and-replace through the entire code. See [ this Wikipedia section](https://en.wikipedia.org/wiki/Magic_number_(programming)#Unnamed_numerical_constants) if you're not familiar with magic numbers.

I'm not sure if pinging the default gateway (option 3) always translates to "testing connectivity to the outside of your local network". It may be so if you're connected directly to the Internet, but here my gateway is my router. Likewise, when I'm connected to a VPN my gateway is 0.0.0.0 (localhost).

Whether to keep within 80 columns is good practice but not always easy to do, especially in shell scripts where you can't (to my knowledge?) easily concatenate multi-line strings properly without removing indentation first.

---

