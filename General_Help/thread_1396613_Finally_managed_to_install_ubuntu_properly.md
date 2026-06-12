---
title: "Finally managed to install ubuntu properly"
date: 2010-02-02
forum: General Help
---

### Post by aviramof on 2010-02-02
properly mean with dual boot ubuntu and seven the way i did it was to simply install ubuntu 8.10 not 9.10
9.10 has a lot of problems i think i had problems with dual boot and internet.

any way now that i have ubuntu installed properly i would be happy if you would help me with some 
simple things.

1.how can i change the dual boot menu default os to be windows 7 i like ubuntu but i still want 7 to be
my default os at least for now.

2.how can i auto arrange files on desktop the option clean by name is fine but it's not automatic.

3.how can install codecs to this os.

4.how can i update firefox to 3.6 

5.how can i install roboform in this os  via wine or something similer i'v found a guide about ies4 linux need help with that.

how can i open url files i have some url from windows i'v tried opening them in firefox but it open firefox download manager. 

if you can help me with at least of  this problems or give me more information about other things that would be great.

thanks in advance.

---

### Post by oldfred on 2010-02-02
I can help with a couple of things;

1. find windows entry in this and copy
gedit /boot/grub/grub.cfg
and copy here but use your windows entry to replace red entry as shown.
gksudo gedit /etc/default/grub
GRUB_DEFAULT="[COLOR=Red]Windows Vista (on /dev/sda1)[/COLOR]"

current entry is 
GRUB_DEFAULT=0

3. Extras:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

4. There have been a lot of posts on installing 3.6. You can search forum for them. But if it is not a default install it is more advanced to set it up. It should be the default with the next release end of April.

When I was converting to Ubuntu I created a shared partition NTFS (now, then FAT) and put firefox and thunderbird profiles in that partition so mail and browser were identical in both systems. When different versions of application only issue was some addins would complain (ubuntu addin did not work in windows etc) but everything else worked fine.

[http://www.mozilla.org/support/thunderbird/profile#locate](http://www.mozilla.org/support/thunderbird/profile#locate)
[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

### Post by marshmallow1304 on 2010-02-02
For .url files: [http://ubuntuforums.org/showpost.php?p=3276774](http://ubuntuforums.org/showpost.php?p=3276774)

---

### Post by aviramof on 2010-02-02
thanks for the help i'v managed to change the boot by using sudo gedit /boot/grub/menu.lst over there 
i edited the vista/longhorn to 7 and for the boot order i used sudo apt-get install startupmanager in the
end because i didn't wanted to risk destroying the dual boot in the end.

---

