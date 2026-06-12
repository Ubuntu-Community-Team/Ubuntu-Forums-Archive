---
title: "bash - execute script before network turns off?"
date: 2011-09-20
forum: General Help
---

### Post by azredwing on 2011-09-20
I'm trying to create some really cool synergy between my computer and my Android phone. Essentially, the two should always be aware if one is on the same network as the other, regardless of what network that might be.

That said, when my computer disconnects from the network (either due to shutdown or due to manual disconnect), the very last thing that should happen is to write a command to my phone via ssh. (I already have keys set up to do no-password ssh, and will be setting up dynamic DNS soon enough).

I have the following script in /etc/network/if-down.d:

```

#!/bin/sh

ssh ipaddr "touch /sdcard/IMOFFNOW.txt"

```

but when I turn off my network, this doesn't execute - my phone never gets IMOFFNOW.txt written to it. I can certainly ssh just fine; it looks like the network is going down too fast for the ssh command to run. (FWIW, I'm just using NetworkManager to connect/disconnect.) 

Scripts in /etc/network/if-up.d work just fine (there, I'm writing my SSID and IP information to Dropbox). 

Hope someone can help me with this? Thanks!

---

### Post by raja.genupula on 2011-09-20
```
ifconfig
``` 
will shows the network connections of you

```
sudo ifdown eth0
```

makes disable your eth0 connection 
so place it as a last line of your script to disconnect your net .

---

### Post by azredwing on 2011-09-20
> **raja.genupula said:**
> ```
ifconfig
``` 
will shows the network connections of you

```
sudo ifdown eth0
```

makes disable your eth0 connection 
so place it as a last line of your script to disconnect your net .

That's not my problem - my problem is, when bringing down the network my script does not execute - or if it does, the network is coming down while the script executes (and thus I can't ssh out). I want to run the command and wait for it to finish executing before the network comes down.

Also, as this is only for wireless - ifdown on eth0 doesn't do anything for me, and ifdown on wlan0 returns the following error:

```

Ignoring unknown interface wlan0=wlan0.

```

Finally, I would prefer to connect/disconnect via Network Manager and not command line, but the script still executes in the background.

---

### Post by staticd on 2011-09-20
Is the script actually running? Before the network is turned of? try adding
```

date>>/tmp/IactuallyRan.txt
ifconfig>>/tmp/IactuallyRan.txt
whoami>>/tmp/IactuallyRan.txt

```

Are the passwordless ssh keys in your home folder or the root's? the script most probably run as root. 
you will have to set up password less ssh from your root account to that of the android phone.

If that isn't the problem,

How about adding a 
```
sleep 1
```
to the script after the ssh?

Good luck! what you'r doing sounds cool. Please do post the results and the details here!

---

### Post by dcstar on 2011-09-20
> **azredwing said:**
> 
That said, when my computer disconnects from the network (either due to shutdown or due to manual disconnect), the very last thing that should happen is to write a command to my phone via ssh. (I already have keys set up to do no-password ssh, and will be setting up dynamic DNS soon enough).

I have the following script in /etc/network/if-down.d:
.........

Executable entities in the folder are processed in lexical order by **run-parts**, if you want this script run first before other things stop rename it so it is at the top of the list.

---

### Post by azredwing on 2011-09-20
> **staticd said:**
> Is the script actually running? Before the network is turned of? try adding
```

date>>/tmp/IactuallyRan.txt
ifconfig>>/tmp/IactuallyRan.txt
whoami>>/tmp/IactuallyRan.txt

```

Are the passwordless ssh keys in your home folder or the root's? the script most probably run as root. 
you will have to set up password less ssh from your root account to that of the android phone.

If that isn't the problem,

How about adding a 
```
sleep 1
```
to the script after the ssh?

Good luck! what you'r doing sounds cool. Please do post the results and the details here!

Those commands work. I decided against ssh and opted instead to send my phone a text message via Perl and Email::Send::Gmail. I'll test that next. I tried using wicd instead but I'm having issues with predisconnect scripts not running there, either. 

Something odd about your script though - it looks like it's running the script twice.. (and yes, I did delete the file before I tried again!) 

> **dcstar said:**
> Executable entities in the folder are processed in lexical order by **run-parts**, if you want this script run first before other things stop rename it so it is at the top of the list.

This did not seem to be the problem - see above. That script ran just fine.

---

### Post by azredwing on 2011-09-20
Got it!

I ended up using wicd to run my pre[dis]connect scripts (I liked wicd better than NetworkManager anyhow, but I never got around to installing it when I got a new computer some time ago). See [this site]("http://wicd.sourceforge.net/moinmoin/Adding%20pre%20and%20post%20(dis)connection%20scripts"). 

I decided to have my computer send a text message to my phone instead of ssh in; this is much more straightforward than the ssh route (issues with dynamic dns and whether I can shell in if my phone is on mobile data).

I wrote the following Perl script to send an email from my computer to my phone's SMS service:

```

#!/usr/bin/perl

# laptopSMS.pl - send the SSID and IP address of the laptop to a cell phone

use strict;
use warnings;

use Email::Send;
use Email::Send::Gmail;
use Email::Simple::Creator;

my $addy = q{helloworld@gmail.com};
my $pass  = q{mypass};
my $sms   = q{myphonenumber@tmomail.net};

my $email = Email::Simple->create(
      header => [
          From    => $addy,
          To      => $sms,
          Subject => "$ARGV[0]", # contains "connected" or "disconnected"
      ],
      body => "$ARGV[1] / $ARGV[2]", # contains SSID and IP, or "disconnected" and "disconnected"
  );

  my $sender = Email::Send->new(
      {   mailer      => 'Gmail',
          mailer_args => [
              username => $addy,
              password => $pass,
          ]
      }
  );
  eval { $sender->send($email) };
  die "Error sending email: $@" if $@;

```

My post-connect script contains the same script as in the link above; appended to it is:

```

if [ "${connection_type}" == "wireless" ]; then

    ipaddr=`ip addr | grep inet[^6] | grep -v 127.0.0.1 | awk {'print $2'} | sed 's!/[0-9]*!!g'`
    /home/cchu/bin/laptopSMS.pl "connected" "$essid" "$ipaddr"

fi

```

And pre-disconnect:

```

if [ "${connection_type}" == "wireless" ]; then
    ~username/bin/laptopSMS.pl "disconnected" "disconnected" "disconnected"
fi

```

Now that my phone is receiving my connection information, I need to use it. I'm using [Tasker]("http://tasker.dinglisch.net/") to do this. Tasker lets you automate your phone based on context (time, date, event, etc). I think of it as a scripting language for Android. Anyhow, I store the computer's SSID and IP to Tasker variables, then run a ping to see if the phone can see the laptop. If it does, I do stuff like turn on wireless ADB, turn on DeskSMS notifications, and if I'm connected to power and on a *preferred* wifi, do an rsync of my phone's SD card.

---

### Post by azredwing on 2011-09-20
I'm now hitting a problem where my computer hangs upon shutdown; I believe is this due to my pre-disconnect script. If anyone has advice please let me know..

EDIT: It was wicd in general, actually. I reinstalled NetworkManager and will rewrite my hooks; the main perl script is staying alive, though.

EDIT2: Post-up script works; pre-down (send another text message) does not. Not sure what's going on here.

---

### Post by deckoff on 2011-10-30
As far as I got it, adding a script into:
```
 /etc/network/if-down.d:

```
will execute AFTER the network is down. The only reliable way I found to do this up till now is WiCD. Unfortunately, it is too buggy for me with 11.10
Still looking for a way to fix this, please report if you find better way

---

