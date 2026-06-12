---
title: "Gnome-panel won't show when using Below window rule plugin from compiz"
date: 2010-04-30
forum: General Help
---

### Post by Axzercion on 2010-04-30
Didn't exactly know where to post this so I thought I would post it here. While I was using ubuntu 9.04, I always found it handy to put the gnome-panel in the Below rule of the Window Rules plugin of compiz. However using this trick doesn't work anymore in Ubuntu 10.04 and I would really like to have this function to a working degree again without too much hassle of having to start/stop compiz or completely reset the gnome-panels.

This is as far as I've gotten on the matter:
Using the Grab function to get the value doesn't work anymore.
Manually inserting the value still works and the function still works after the manual insert.
When inserted and after a reboot the top gnome-panel isn't loaded anymore.
A restore of the gnome-panel using pkill gnome-panel doesn't work.
After disabling the window rule and messing around a bit you can get the gnome-panel back, but this requires atleast 1 reboot.

This got me thinking to writing a script that disables the window rule on shutdown/restart and then another script that would re-enable the window rule on login. Unfortunately I haven't had much luck doing that since I'm not that great a scripter.

I found out that using the gconftool you can unset the value of the key in gconf. I've made the following script to get it to work:
#!/bin/bash
gconftool -u /apps/compiz/plugins/winrules/screen0/options/below_match

exit

For some reason using sudo bash <script> doesn't work, but bash <script> does. I think this has to do with me being a user and that it is somehow locally managed but obviously the sudo affects the entire system instead of specifically my account. I've read somewhere that the script has to be put into the rc0.d and rc6.d folders in the /etc/ folder, but seeing as the sudo command doesn't work I've had little luck in getting this script to work.

Can someone help me write these scripts and get them to run?

Edit: found the solution after a long time...
install wmctrl, create a bashscript looking like this:
#!/bin/bash
process_found=false
while [ $process_found == false ] ;
do
sleep 1
pid=`ps -eo pid,args | grep 'gnome-screensaver' | grep -v grep | cut -c1-6`
if [ "$pid" != "" ] ; then
process_found=true
fi
done
sleep 5
wmctrl -r "Bottom Expanded Edge Panel" -b remove,above -b add,below
exit 0

And add that to start-up

---

