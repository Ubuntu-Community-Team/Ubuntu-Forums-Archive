---
title: "NTP Issues."
date: 2011-04-08
forum: General Help
---

### Post by Roasted on 2011-04-08
I'm running several Ubuntu servers with LTSP thin clients in our classrooms. It's been a royal pain trying to get them to synchronize time properly. Currently I'm looking at 7 client's login screen and each one has different time. It's frustrating and I've done all the reading I could in regard to NTP and LTSP with time, etc.

Can anybody shed some light on what I can do here? I'm trying to even set NTP to point to an external server, but my thin clients don't get that setting for some reason. They still pick whatever time they want to present to the end user. Once the user logs in, the time seems to be fine. It's just at the login screen.

Since I'm no expert on NTP I figured I'd ask to see what users here thought. What could possibly be wrong?

EDIT - I was told that the GUI version of Ubuntu handles NTP at System-Administration-TimeAndDate. Is this true? I was told my /etc/ntp.conf file is empty because that file is only used in the server edition of Ubuntu.

---

### Post by Roasted on 2011-04-09
uppppppppp

---

### Post by SeijiSensei on 2011-04-09
I thought the clients in LTSP did nothing but display sessions off the server.  If they display different times, doesn't that mean the *servers* aren't synchronized?

Each server needs to run ntpd.  Have one of them sync to [external time servers]("http://support.ntp.org/bin/view/Servers/WebHome") like 0.pool.ntp.org.  Have all the other servers use that one as their time server.

You may want to run "hwclock --systohc" on each machine after they've synchronized to make the internal hardware clock match the time obtained from NTP.  I usually add an entry to /etc/crontab to run that command once a day given the notorious unreliability of PC hardware clocks.

---

### Post by Roasted on 2011-04-09
Technically the clients do, however by default the time entry is unset in LTSP land, so therefore the clients look to their hardware clocks unless otherwise specified.

"Otherwise specified" basically included adding a time entry in your lts.conf which controls the thin clients behavior. I did that, but it seems as if it's not syncing. However further reading later on suggested time sync may take upwards of 2 hours. Is that true? Could time sync take that much time? I assumed time was a quick thing. Secondly, do you have any idea about the "time and date" entry in the GUI under System - Administration? Is that where the /etc/ntpd.conf is in the GUI version, while the server version of course has it in /etc/ntpd.conf? Just trying to learn what I can while we're on the topic. :)

---

### Post by SeijiSensei on 2011-04-09
> **Roasted said:**
> Technically the clients do, however by default the time entry is unset in LTSP land, so therefore the clients look to their hardware clocks unless otherwise specified.

I have no experience with LTSP, just a general sense of how it works from reading a few things at ltsp.org.  It does sound like the hardware clocks are unreliable, so running "hwclock --systohc" each hour or so from /etc/crontab might help.

> However further reading later on suggested time sync may take upwards of 2 hours. Is that true? Could time sync take that much time? I assumed time was a quick thing.

If you run the ntpdate client, it will update the time from the network immediately.  ntpd itself can take longer initially because it first spends some time watching the hardware clock and comparing it to the network time signals.  Two hours seems unreasonably long, though.  I just changed my server in /etc/ntp.conf and restarted ntpd.  It waited about five minutes or so, then updated the time from the server.

> Secondly, do you have any idea about the "time and date" entry in the GUI under System - Administration? Is that where the /etc/ntpd.conf is in the GUI version, while the server version of course has it in /etc/ntpd.conf? Just trying to learn what I can while we're on the topic.

On this machine, which is a client, I have an /etc/ntp.conf file.  I also appear to have ntpd running, so I'm guessing that's the file ntpd is using.

You might also need to permit UDP port 123 on your firewall so the local master server can communicate with the remote time servers.

---

### Post by tgalati4 on 2011-04-10
You could also set up a server to run ntp and advertise as a time server on the local network, using the broadcast setting.  My ntp.conf is rather complicated.  It keeps time to within 1 or 2 milliseconds of the master clocks.


tgalati4@tubuntu2:/etc$ cat ntp.conf
# Updated 20 Oct 08 to add new servers
logfile /home/tgalati4/ntp_stuff/ntp_trace.log
driftfile /var/lib/ntp/ntp.drift
# The next 4 lines adds statistics to /var/log/ntpstats--hopefully
statistics loopstats peerstats #  clockstats
statsdir /var/log/ntpstats/
filegen peerstats file peers type day link enable
filegen loopstats file loops type day link enable
# filegen clockstats file clockstats type day link enable
server tick.cs.unlv.edu
server tick.mtnlion.com
#server tick.jpunix.net
server ntp1.stsn.net
server north-america.pool.ntp.org
server time.apple.com
# Beef up security policy--see hpubuntu's /etc/ntp.conf
restrict default kod notrap nomodify nopeer noquery
restrict 127.0.0.1 nomodify
broadcast 192.168.1.255

I don't know if the LTSP kernels read the network broadcast time.  That is something you will have to research.  I presume that you will have to have ntpd running on each LTSP client.

---

### Post by Roasted on 2011-04-10
> **tgalati4 said:**
> 

I don't know if the LTSP kernels read the network broadcast time.  That is something you will have to research.  I presume that you will have to have ntpd running on each LTSP client.

But technically, it being on the server = it being on the thin client, since the clients just generate sessions from the server... 

I'll try running the ntpdate client command and see if that jumps them up to speed with the proper time. 

What's interesting is once you log in, the Gnome applet clock shows the proper time. It's at the login screen where there's a little digital clock in the corner that is clearly off.

---

### Post by tgalati4 on 2011-04-10
Is it off by UTC versus local time?  If so, then UTC is stored in the hardware clocks of each client.  The UTC offset (which is local time) doesn't get set until the user logs in.  Each user can set up their own timezone.  There's a way to set local time to the BIOS, but I don't know it offhand.

---

### Post by Roasted on 2011-04-11
> **tgalati4 said:**
> Is it off by UTC versus local time?  If so, then UTC is stored in the hardware clocks of each client.  The UTC offset (which is local time) doesn't get set until the user logs in.  Each user can set up their own timezone.  There's a way to set local time to the BIOS, but I don't know it offhand.

We do set the time at the BIOS level offhand. We also lock the BIOS with a password since, after all, we're in a school and you never know what high schoolers might get up to. ;)

The time can be off by any number. The most common is 3 hours, which would be Pacific time whereas I'm in Atlantic time. It's in military time, and the other day I noticed a whole array of different times on the workstation lab of 8 systems in the library, which goes something like this:

19:14
19:14
19:15
18:32
23:14
21:30
20:14

So while I did have some in the ballpark with hours + minutes, and others were in the ballpark with at least minutes (even if their hour setting was off) I still had a few quirks coming out of left field, such as the 20, 21, and 23 times above.

---

### Post by Roasted on 2011-04-13
Upon some further discussion with some LTSP developers, it sounds like it may be a minor bug on their end. There is some testing to be done to try and figure it out, but ultimately my NTP was set up fine all along... it was just something else in regard to the way NTP is handled with server/client environments with LTSP. I'll post back if there is ever a definitive answer.

---

### Post by Evilware on 2011-08-09
Hi there, I know this is an older issue, but I am running about 120 LTSP fatclients, and like you getting the time correct on each work station is a pain, but here is what I did

in /opt/ltsp/i386/etc/X11/Xsession.d/
I added my own run level 60 init
60int
####
#!/bin/sh

GROUPS=`groups $USER`
for GROUP in $GROUPS
do
if [ $GROUP = "mygroup" ];
then
/usr/share/ldm/themes/custom/scripts/mycustomscipt $USER
else
/usr/share/ldm/themes/custom/scripts/myotherscript
fi
done

in /opt/ltsp/i386/usr/share/ldm/themes/custom/scripts/mycustom/scripts/
contents of mycustomscript (stripped for this)
#########
#!/bin/sh

ntpdate (dns name or IP of timeserver)
in my case its
ntpdate 10.20.250.200

#####

Granted for thin clients I think its easier
add an entry into
var/lib/tftpboot/ltsp/i386/lts.conf

TIMESERVER = (ip of timeserver)
RCFILE_01 = /etc/ltsp/ntpdate

in /opt/ltsp/i386/etc/ltsp/ntpdate
you just need
#!/bin/sh
ntpdate YOURTIMESERVER

make sure its executable and readable.

---

