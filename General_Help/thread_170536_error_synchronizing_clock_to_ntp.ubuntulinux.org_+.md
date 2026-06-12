---
title: "error synchronizing clock to ntp.ubuntulinux.org + network connection problem"
date: 2006-05-04
forum: General Help
---

### Post by pongu on 2006-05-04
i'm new and have a problem. a big surprise, i'm sure. i'm on a compaq v2030us laptop dual booting xp and ubuntu. i kind of have two problems that seem to be working together.

first, during boot it hangs when "synchronizing clock to ntp.ubuntulinux.org" for a long time until it finally gives up and says "error: temporary failure in name resolution." i've read several threads trying to find a solution and have made no progress. i can hit ctrl+c to skip it but i'd rather not have to do that.

secondly, once my system boots up, my wireless does something funny. it says it's connected but it won't let me access the internet until i select my location from the networking dialog. after i select my location it's fine. i don't know how to make the location default so it connects automatically. it seems this connection problem would be the reason the clock synchronization hangs during boot. how can i make it connect properly and earlier during boot?

laptop specs if needed:
[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00248733&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00248733&lc=en&jumpid=reg_R1002_USEN)

---

### Post by Jimmey on 2006-05-04
You're right in assuming that the failure of the name resolution is linked to the lack of internet access when you boot up. Your computer, when it boots, tried to contact ntp.ubuntulinux.org to try and recover the correct time :) (Unless I'm mistaken). 

As a result of the computer's failure to properly connect to the internet on boot, your computer can't reach ntp.ubuntulinux.org, and as a result of this, can't check the time.

With regard to the location properties in the networking dialog - Are there more than one locations? Is that really necessary?

If it's not, I suggest that you delete one ( only because I've no idea how to set them up correctly :P )

Thanks

---

### Post by pongu on 2006-05-04
it's good to know that my problems are linked but sadly i still have no resolution. i had two network locations. i deleted one and rebooted but nothing changed. it still couldn't synchronize the clock and i still couldn't access the internet until i selected my location from the networking dialog. i read in other threads about people having difficulty with ntp.ubuntulinux.org hanging but their problems didn't seem to match mine entirely. some of them could resolve it by changing the site with which the clock synchronizes. but, as you agreed, i think my problem is the lack of internet connection during boot. of course, once/if i get that resolved i'll know more about whether or not it's linked to my clock synchronization hang.

if there's no other resolution, would it hurt to disable this boot service?

---

### Post by Jimmey on 2006-05-06
It wouldn't hurt to disable the synchronisation with the NTP server at boot, no. As I don't have the answer, and no-one else seems to be replying, you may want to try the Ubuntu IRC channel ( #ubuntu ) on freenode.

---

### Post by pongu on 2006-05-06
thanks for your assistance. i'll try that.

---

### Post by ZiLOG_Z80 on 2006-05-06
One way to prevent the clock synchronization at startup is to edit /etc/default/ntpdate and comment out all of the ntpservers. I dont know if this is the best way but it seems to work.

---

### Post by pongu on 2006-05-06
my problem is i don't know how to do that. i'm dual booting linux because linux is what is used where i work. so i'm beginning to teach myself command. i know how to disable ntpdate on boot but i've read that it could cause my clock to get off by an hour every time i boot up. if you want to walk me through how to comment out all the ntpservers then i'm willing to listen. otherwise, i'll just keep manually skipping the boot service until i get far enough in learning command to be able to modify these things myself. it's rather annoying having to skip it every time during boot so i thought i'd see if anyone could help. it's also annoying--to you and to me--having to ask all these questions in forums. i like being able to do these things myself rather than rely on others. it's not fun being in the beginner stages.

---

### Post by ZiLOG_Z80 on 2006-05-07
To edit the file you need to use a text editor under supper user privilages. You can do that by typing ```
sudo gedit /etc/default/ntpdate
``` You may need to use a different editor to gedit if you're not using Ubuntu (I think its Gnome specific) though I cant be sure as I'm a beginner to and only have experience with Ubuntu. My ntpdate looks like ```
# servers to check.   (Separate multiple servers with spaces.)
#NTPSERVERS="pool.ntp.org"
#NTPSERVERS="ntp.ubuntulinux.org"
#
# additional options for ntpdate
#NTPOPTIONS="-v"
NTPOPTIONS="-u"

``` after commenting out the server using #

---

### Post by rcarring on 2006-05-07
If you are running that edit command from the shell, suggest you substitute pico or nano for gedit, as gedit is NOT installed by default.

CTRL -O to write the file, CTRL- X to exit pico / nano

If it won't let you save the file then you need to sudo pico {path and name of file}

---

### Post by pongu on 2006-05-07
thanks ZiLOG_Z80 for the help. the boot is much quicker now. i still have my wireless connection annoyance but i guess i'll deal with it for now. whenever someone shows me how to do these things i often feel stupid because what i want is usually quite simple. thanks for helping and not being condescending.

---

### Post by electroconvulsive on 2006-05-08
Thanx Zilog I had the same problem and dnow I dont anymore.

---

### Post by ZiLOG_Z80 on 2006-05-08
glad to be assistance. we were all green once. I'm still pretty green myself, but if we all share the solutions to the problems we find, life will be a lot easier for everyone

---

