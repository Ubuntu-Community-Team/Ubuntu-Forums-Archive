---
title: "NTP Question"
date: 2012-07-25
forum: General Help
---

### Post by doublez2 on 2012-07-25
I just installed the NTP Server on my Ubuntu Server. I'm just wondering whether NTP syncs automatically with the servers in the configuration file, or if I have to manually sync them

---

### Post by Cheesehead on 2012-07-25
It should work automatically.

Use the command [FONT="Courier New"]ntpq -p[/FONT] to check if synchronizations are really happening and how often.

---

### Post by doublez2 on 2012-07-25
I ask because when you do /etc/init.d/ntp start, your supposed to see a line in the syslog about how it synced with a another time server. But I haven't seen that line. I ran your command and it seems to be communicating with all the higher NTP servers

---

### Post by Lars Noodén on 2012-07-26
You could force a synchronization with [ntpdate](http://manpages.ubuntu.com/manpages/precise/en/man8/ntpdate.8.html).  If your clocks are badly off then look at using the -b option.

---

### Post by doublez2 on 2012-07-28
is there anyway I can tell that their synchronizing.

---

### Post by Lars Noodén on 2012-07-28
You see if they're synchronizing by checking [font=Courier New]/var/log/syslog[/font].  You can [grep](http://manpages.ubuntu.com/manpages/precise/en/man1/grep.1posix.html) for 'ntp'  If it's synchronizing you'll see little messages like this:

```

Jul 28 10:04:23 lubuntu ntpdate[1415]: step time server 62.236.120.71 offset -1.569216 sec

```

Edit: that was ntpdate, but you'll see somewhat similar for ntp if adjustments are being made.  ntpdate gets run at boot.

---

