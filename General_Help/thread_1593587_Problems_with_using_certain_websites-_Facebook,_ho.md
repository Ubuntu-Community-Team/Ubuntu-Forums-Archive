---
title: "Problems with using certain websites- Facebook, hotmail etc."
date: 2010-10-11
forum: General Help
---

### Post by voguebanana on 2010-10-11
I installed Ubuntu (the newest version) onto my Toshiba laptop to replace Windows Vista Premium. However, since installing it I cannot use some website on Mozilla, these include: Facebook, hotmail, wikipedia, ebay and 4od. Either they never load or they load up first time round but cannot be refreshed. I can't seem to find any clear advice anywhere online for this problem, am I the only one to experience it?
The Instant messaging program also refuses to work. 

Any advice would be hugely appreciated, thanks :)

---

### Post by Tristan Tonks on 2010-12-22
This is a test because I just sent one post which went but I have a larger one which will not --- will this one go ....?

---

### Post by Tristan Tonks on 2010-12-22
Ok, If this post goeas then the problem may be something to do with mtu (Maximum Transfer Unit)

---

### Post by Tristan Tonks on 2010-12-22
I have been battling this problem for ages - ever since Karmic came out. Some times you can get round it in the first instance by doing a crtl + delete to clear all your cookies but not always, It is very frustrating, I dont have ipv6 running anymore so I know it's not that.

Check your ipv6 by running;

ip a | grep inet6

in terminal if there is no output then it is off. If it's still on check this thread which should turn it off;
[http://ubuntuforums.org/archive/index.php/t-87798.html]("http://ubuntuforums.org/archive/index.php/t-87798.html")

If you are running Lucid Lynx you will need to do this;

open your terminal and;
-----------------
[FONT="Arial"]sudo gedit /etc/sysctl.conf[/FONT]
-----------------
add the following lines to the bottom of the file;
-----------------
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
-----------------
save and close the file.......go back to your terminal and again;
-----------------
ip a | grep inet6

this time it should return empty (it just goes back to prompt)

Now can someone who knows what they are talking about please help us out from here?  :D

---

### Post by Tristan Tonks on 2010-12-22
Ok, Finally I think I have sorted it :

This is an mtu problem, in system-network-network conections select your connection type from the tabs;

Mine was wireless,

Now select your actual connection from the list .... 
select Edit button at the side.
At the bottom you will see a field marked MTU: _____ it will likely be set to automatic, clearly the automated aspect of this is not being set - this could be a setting somewhere else that is incorrectly set but by choosing the correct number for this entry you should solve the problem.
For wireless the number will be 1492 then click apply and close.
if not try these consecutively; 1492,1454,1452,1460

You should be able to access that troublesome site with at least one of them.

For the record this should be a much easier thing to solve and may not be the whole story ... this thread should be linked to the other threads about this topic and cleaned up a bit.

I feel help will still be needed on this ...

---

### Post by amjjawad on 2010-12-22
> 			October 11th, 2010 			 			

More than two months now ;)

---

