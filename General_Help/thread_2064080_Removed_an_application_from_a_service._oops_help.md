---
title: "Removed an application from a service. oops help"
date: 2012-09-28
forum: General Help
---

### Post by wt9bind on 2012-09-28
A bit of background:

I have had mediatomb installed on my machine for some time now, anyway today it was messing up so I decided to remove it in which I did.

I re-installed it and went to start it using:
sudo /etc/init.d/mediatomb start

I received the following message:


Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mediatomb start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mediatomb
mediatomb start/running, process 3083

No probs I think, everything is sweet, however when heading to [http://server:49152](http://server:49152) it doesn't work. I just get a this page cannot be displayed message.

So I head back and type: sudo /etc/init.d/mediatomb stop
And it says something like the process cannot be found or the likes (sorry vague on this part)

So I think, hrm, the service is messing up so I follow the instructions at: [https://help.ubuntu.com/community/MediaTomb#Running_MediaTomb_Manually](https://help.ubuntu.com/community/MediaTomb#Running_MediaTomb_Manually)

It returns the following:

 sudo mv /etc/init.d/mediatomb /etc/init.d/mediatomb.backup


 sudo update-rc.d mediatomb remove
 Removing any system startup links for /etc/init.d/mediatomb ...

I then run mediatomb, low and behold mediatomb starts and runs. Yippee!!

Now, I want it to run as a service again, so I assume that I type:
 sudo mv /etc/init.d/mediatomb.backup /etc/init.d/mediatomb

sudo update-rc.d mediatomb defaults

Which gave me:
sudo update-rc.d mediatomb defaults
update-rc.d: warning: /etc/init.d/mediatomb missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/mediatomb ...
   /etc/rc0.d/K20mediatomb -> ../init.d/mediatomb
   /etc/rc1.d/K20mediatomb -> ../init.d/mediatomb
   /etc/rc6.d/K20mediatomb -> ../init.d/mediatomb
   /etc/rc2.d/S20mediatomb -> ../init.d/mediatomb
   /etc/rc3.d/S20mediatomb -> ../init.d/mediatomb
   /etc/rc4.d/S20mediatomb -> ../init.d/mediatomb
   /etc/rc5.d/S20mediatomb -> ../init.d/mediatomb

I then try 


sudo /etc/init.d/mediatomb start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mediatomb start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mediatomb
mediatomb start/running, process 3240

Oh great, its running on process 3240, so I head to webmin and I can't see that process, so I head back to CLI and type:


 stop mediatomb
and get the following:
stop: Unknown instance:


So I have learnt a valuable lesson here, ask before trying to fix the problem myself.

The thing is now, I really would like mediatomb to start as a service again now I know it is working fine.

Please help :)

Thanks 

P.S Really hope I have posted to the correct area, I know it is more of a mediatomb question but I feel this is a syntax error I must be doing with setting a service for any application, let alone mediatomb.

---

