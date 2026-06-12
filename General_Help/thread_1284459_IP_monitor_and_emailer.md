---
title: "IP monitor and emailer?"
date: 2009-10-06
forum: General Help
---

### Post by MarkX on 2009-10-06
Hello folks!
I need a prog, preferably with GUI, which emails my dynamic IP to my email every time it changes (so I can access my security cams, for example or use remote desktop). There are numerous such IP mailer progs for windows but is there an equivalent one for Ubuntu please?

(I don't want to use dyndns. It closes free accounts if they are not used for a month and I don't want/need to rely on some other company!)

---

### Post by StuartN on 2009-10-06
> **MarkX said:**
> preferably with GUI

I don't know about a GUI, but there is a neat idea using **wget -q [http://checkip.dyndns.org/](http://checkip.dyndns.org/)** to save your current IP address and send it by SMS. You could probably adapt this script to use Mutt instead:

[http://ubuntuforums.org/showthread.php?t=373963](http://ubuntuforums.org/showthread.php?t=373963)

---

### Post by t0p on 2009-10-06
Although you don't want to use DynDNS, you might be able to use one of the [update clients]("http://www.dyndns.com/support/clients/") that it recommends.  If that's not possible, or if it does not suit, you can still use checkip.dyndns.org to check if your IP has changed.  Install **curl**.  Now you can check your IP with the following command:

```
curl -s http://checkip.dyndns.org | sed 's/[^0-9.]//g'
```You could incorporate that into a script.  Then, if the IP has changed, the script could send you the new IP via email (I would use **exim4** and a Gmail server for this, as described [here]("http://wiki.debian.org/GmailAndExim4")).

I've been pondering this very subject for a while now, but haven't yet actually set to writing the script.  If you write a script, or if you find an easier way to do this, I would very much like to know.

---

### Post by MarkX on 2009-10-06
I wouldn't know where to start writing my own stuff, plus I don't want to, it's not my hobby.

It just needs a little GUI which says:

Email IP to:
1)...........
2)...........

X on change
X every: ...day/s, ..hours, ..minutes

The IP could be displayed in the email subject title so it doesn't even have to be opened and can be copied and pasted.
Like this:

IP= [http://123.123.123.123](http://123.123.123.123)

That little feature could be integrated into various other apps including email programs like Thunderbird or webcam surveillance progs or whatever. (Ideally routers should be equipped with this function, on top of dydns.)

---

### Post by t0p on 2009-10-06
Google turns up a couple of tools which may suit.  There's [XSS IP Monitor 1.8]("http://wareseeker.com/free-ip-monitor-linux/"), and [MSA IP Monitor 1.1.2]("http://wareseeker.com/Network-Tools/msa-ip-monitor-1.1.2.zip/7c5cda9d4").   I haven't tried either program, but the descriptions sound suitable.

**EDIT:** Actually these programs appear to be Windows only.  ******* stupid search engines!

---

### Post by MarkX on 2009-10-06
> **t0p said:**
> Google turns up a couple of tools which may suit.  There's [XSS IP Monitor 1.8]("http://wareseeker.com/free-ip-monitor-linux/"), and [MSA IP Monitor 1.1.2]("http://wareseeker.com/Network-Tools/msa-ip-monitor-1.1.2.zip/7c5cda9d4").   I haven't tried either program, but the descriptions sound suitable.

**EDIT:** Actually these programs appear to be Windows only.  ******* stupid search engines!

Yup, (they also cost money)!
 There are heaps of them for windows but I have found none for Linux, which is kind of strange. Without an IP all manner of programs become useless.
I would have though it would be just the kind of really useful app a linuxer or unix admin would throw together in a coffee break to get their dynamic home IP.

---

### Post by brian mcgee on 2009-10-06
Did a quick search and found this:

[http://onthefencedevelopment.com/?p=289](http://onthefencedevelopment.com/?p=289)

---

### Post by t0p on 2009-10-06
You might like to look at [arpwatch]("http://techgurulive.com/2008/09/15/how-to-monitor-and-be-informed-of-ip-address-changes-from-your-network/") and [PHP Open Monitor]("http://phpopenmonitor.sourceforge.net/").

---

### Post by t0p on 2009-10-06
> **brian mcgee said:**
> Did a quick search and found this:

[http://onthefencedevelopment.com/?p=289](http://onthefencedevelopment.com/?p=289)

Now that looks good!  I'm going to have something to eat, then I'll see what's what... but at a glance it seems to be what we want.

**EDIT:**  Yeah, I can use that script, but instead of doing the Twitter thing I can [use exim4 and Gmail]("http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/") to send myself the IP address via email.  Sweeet!!

---

### Post by StuartN on 2009-10-07
Just an idle thought, but isn't your current IP address in the last Received: header in any email you send? If so, then all you need is to send a daily email by cron.

---

### Post by MarkX on 2009-10-07
> **t0p said:**
> Now that looks good!  I'm going to have something to eat, then I'll see what's what... but at a glance it seems to be what we want.

**EDIT:**  Yeah, I can use that script, but instead of doing the Twitter thing I can [use exim4 and Gmail]("http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/") to send myself the IP address via email.  Sweeet!!

Could you please post the whole thing with instructions please, please?!! This is double dutch to most people.

Or could someone else write the instructions on how to do it please!

---

### Post by StuartN on 2009-10-07
> **MarkX said:**
> Could you please post the whole thing with instructions please, please?!!

Following (various) instructions above, I have tried it with success according to the following steps:

1) Install Mutt. This is the only additional package you need.

2) Configure your outgoing mail server - in my case I have created a new file ~/.mutt/muttrc which contains just two lines:

```
set smtp_url="smtp://my.smtp.server:25/"
set from="Me@My.Domain"
```

Replace my.smtp.server and [email]Me@My.Domain[/email] with your smtp server and your email address. Search for mutt and GMail etc if you use a different outgoing mail server.

3) Create the following script (I called it ip_monitor.sh), save it and make it executable:

```
#!/bin/bash
IPFILE=~/ipaddress
CURRENT_IP=$(wget -q -O - http://www.whatismyip.com/automation/n09230945.asp)
if [ -f $IPFILE ]; then
        KNOWN_IP=$(cat $IPFILE)
else
        KNOWN_IP=
fi
 
if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
        echo $CURRENT_IP > $IPFILE
        mutt -s "My IP is now "$CURRENT_IP me@my.domain < $IPFILE
fi
```

This script will create a file ~/ipaddress containing your IP address, obtained from whatismyip.com, and rewrite this file everytime your IP address changes.

It will send an email address with subject line and body containing the new IP address.

4) Add a cron entry (e.g. by crontab -e) to run this script at regular intervals, the line below would run it at 4:01 am every day:

```
01 4 * * * ~/ip_monitor.sh
```

Emails will only be generated if the IP address changed, not every time the cron job runs.

---

### Post by CharlesA on 2009-10-07
Thank you for the infos. I'm trying to setup a relay to gmail since my notification software won't email me updates for some reason.

Hopefully I can mod this to get the job done. :)

---

### Post by t0p on 2009-10-07
I've been toying with the idea of an ip change notification emailer for a while, but this thread jump-started me into action.  Here's my solution to the problem.

1. Install exim4.

```
sudo apt-get install exim4
```2. Configure exim4 to use a gmail smtp server, by following the instructions [here]("http://wiki.debian.org/GmailAndExim4").  (Don't let all the command-line stuff put you off - it's mostly just copy-and-paste.)

3. I've used the script from [here]("http://onthefencedevelopment.com/?p=289"), with some adjustments - let's call it "checkip":

```
#!/bin/bash
# Checkip by t0p, based on a script by Dave at onthefencedevelopment.com
IPFILE=/home/username/ipaddress
CURRENT_IP=$(wget -q -O - http://www.whatismyip.com/automation/n09230945.asp)
if [ -f $IPFILE ]; then
        KNOWN_IP=$(cat $IPFILE)
else
        KNOWN_IP=
fi
 
if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
        echo $CURRENT_IP > $IPFILE
        cat $IPFILE | mail -s "IP has changed" user@example.com
fi

```4. Make "checkip" executable:

```
chmod +x checkip
```I thnik that's pretty much it.  When you run checkip, it checks the current ip address.  If the ip has changed, checkip sends an email containing  the new ip address.

So all you need to do now is set up a cronjob running checkip at whatever intervals you like.

Enjoy!

---

### Post by spillin_dylan on 2009-10-07
Here was my solution; I wanted the exact same thing, so I went ahead and wrote my own script in Perl, partly because I wanted a script like this, and partly just to try learn Perl.  It's maybe not the prettiest thing around, but it should work for you with minor adjustments.  It also keeps track of all your changes, and when they occurred in an external file.

```

#!/usr/bin/perl
#
#  newipnotify.pl
#
#  A script to send an email/SMS message from the computer it's on, to a specified address
#  anytime the external (web-visible) IP address is changed.  
#
#  Should only be necessary if you have a Dynamic IP assigned by your ISP, and you
#  need to know the IP address for SSH'ing into your server, or something along those lines.
#  This is precisely the reason I wrote it.  Well, that and learning Perl. 
#
#  Should be run by crontab, or scheduled some other way, as it only returns the current IP addy
#  everytime it's run, and appends any changes to .IPaddr file.


# TODO:
# 1) If the file doesn't exist in the first place?  DONE
# 2) Implement mail part of this script...          DONE

use warnings;
use strict;
use MIME::Lite;


my @months = qw(Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec);
my @weekDays = qw(Sun Mon Tue Wed Thu Fri Sat Sun);
my ($second, $minute, $hour, $dayOfMonth, $month, $yearOffset, $dayOfWeek, $dayOfYear, $daylightSavings) = localtime();
my $year = 1900 + $yearOffset;
my $theTime = "$hour:$minute $months[$month] $dayOfMonth, $year";
my $mins = 60;                 # Time in minutes before retries.  Not currently used.

my $recipient = 'put_your_email@address.here';      # \
my $subject =   'New IP';                #  ) Message data
my $comp_name = `uname -n`;              # /
chomp $comp_name;
#my $essid_name = `iwconfig wlan0 | sed 's/  /\n/g' | grep ESSID | sed 's/ESSID:"//'| sed 's/"//'`;
#chomp $essid_name;

my $IPfilename='.IPaddr';      # The filename to use

my $silent = 0;                # Silent mode toggle
my $curdir;                    # Current working directory
my $fileerror = 0;
my $forcesend = 0;
my $debug = 0;                 # Debug mode toggle.
my $i = 0;                     # Counting variable
my $numargs = @ARGV;           
my $IPchanged = 0;             # Toggle if IP has changed
my @ipaddresses;

while ($i < $numargs) {
#   print "\$ARGV[$i] = " . $ARGV[$i]."\n";
   if ($ARGV[$i] eq "-h"){
      print "\nnewipnotify.pl\n\n";

      print "A Perl script to send an email/SMS message from the computer it's on, \n";
      print "to a specified address anytime the external (web-visible) \n";
      print "IP address is changed.\n\n";

      print "Should only be necessary if you have a Dynamic IP assigned by your\n";
      print "ISP, and you need to know the IP address for SSH'ing into your server,\n";
      print "or something along those lines.\n\n";

      print "Usage:\n\n";
      print "   -h, --help         Brings up this page\n\n";

      print "   -D, --DEBUG        Debug mode. Does not make changes to or \n";
      print "                      any files, but simulates results.\n\n";

      print "   -m, --mail         Specify the email address of the recipient\n\n";

      print "   -s, --silent       Silent mode.  Only prints the current IP address.\n";
      print "                      Useful where you want only the IP address.\n\n";

      print "   -f, --force-send   Forces a mail to be sent, whether the IP\n";
      print "                      has changed or not.\n\n";

      exit 0;
   }
   if ($ARGV[$i] eq "-D"){ #
      $debug = 1;
      print "Debug mode ON\n";
   }
   if ($ARGV[$i] eq "-f"){
      $forcesend = 1;
      print "\n";
   }
   if ($ARGV[$i] eq "-s"){
      $silent = 1;
   }
   if ($ARGV[$i] eq "-m"){
      $i++;
      $recipient = $ARGV[$i] if defined $ARGV[$i] or die "Please specify recipient!!";
   }


   $i++;                          # Check next set of parameters.
}

print "Getting IP address..." unless ( $silent == 1);
my $ipaddr = `wget --quiet --tries=5 -O - http://whatismyip.org/ | tail` ;  # Get the IP address, and put it in a variable.
if ( $ipaddr eq "" ) {
   if ( $silent == 1 ){
      print "IP unavailable\n";
   }else{
      print "... failed!  Aborting...\n";
   }
   exit 1;  # Leave an error flag if we didn't get the ip addy....
}
print ".done!   $ipaddr" unless ( $silent == 1);

sub makeIPfile {  
   open (IPfile, ">$IPfilename") or die ("Getip:  Cannot open $IPfilename file for writing.\n");
   print "Writing new file..." unless ($silent == 1);
   print IPfile $ipaddr . " " . $theTime;
   print IPfile "\n";
   print IPfile @_;
   close (IPfile);
   print "done!\n" unless ($silent == 1);
   return; 
};

my $message = MIME::Lite->new(
   To => "$recipient",
   Subject => "$subject",
   Data => "New IP Address on $comp_name is $ipaddr\n\n"
);

# Gets the old file, or makes a file if it wasn't there already.
open (oldIPfile, "<$IPfilename") or makeIPfile(); 
my @oldIPfile = <oldIPfile>;      # Get existing file data
close (oldIPfile);
my @fields;
my $line = $oldIPfile[0]; 
@fields = split(/ /,$line);       # Was going to use this, and compare timestamps, but 
chomp $fields[1];                 # we already have the most recent on top.  Why worry?

# Is the IP different than last time we checked?
if ( $fields[0] ne $ipaddr ){     # Since the last one will always be prepended to the file,
   print " has changed!\n" unless ($silent == 1);     # we can read the first field from the file, and check against that
   $IPchanged = 1;
} else {                          # Otherwise, we're done here until next time!  
   print " hasn't changed." unless ($silent == 1);
   if ( $forcesend == 1 ){        # Send a message anyhow, if "-f" flag set at CLI, probably not a necessary option... but hey  :)
      print "\nSending message..." unless ($silent == 1);
      $message->send('smtp', 'smtp.telus.net', Timeout => 60 );
      print "done!\n" unless ($silent == 1);
   } else {
      if ( $silent == 1){
         print "$ipaddr";
      }else{
      print "  Done.\n" unless ($silent == 1);
      }
   }
   exit 0;
}#end if

# If the IP address has changed, prepend it to the file, and do the mail thing.
if ( $IPchanged == 1 ){
   # Writes the new data to the top of the file
   makeIPfile(@oldIPfile);
   if ( $debug == 1 ){  # Debug mode: Show the email instead of sending.
      $message->print ( \*STDOUT );
   } else {
      print "Sending message..." unless ($silent == 1);
      $message->send('smtp', 'smtp.telus.net', Timeout => 60 );
      print "done!\n" unless ($silent == 1);
   }
}
if ( $silent == 1){
   print "$ipaddr";
} 
exit 0;                           # Success!


```

---

### Post by CharlesA on 2009-10-08
Thank you T0p and spillin_dylan. That's exactly what I was looking for. :-)

I actually ended up setting up exim4 in order to be able to get my raid management software to send emails via gmail.

Now I just need to read up on setting up a cronjob.

---

### Post by MarkX on 2009-10-08
That's all very Dandy for you Linux folk and I'm jolly glad it was so easy for you to get to work but how about something ordinary mortals can make sense of?:confused:
 I'm dumb and need a GUI.:cry:
Is there anyone who can turn this into something that can be downloaded and installed? With some Icon that tells people it's actually running? :(

---

### Post by MarkX on 2009-10-08
> **StuartN said:**
> Following (various) instructions above, I have tried it with success according to the following steps:

1) Install Mutt. This is the only additional package you need.

[COLOR="SeaGreen"]**I could possible do this if it's in "ADD AND REMOVE".**[/COLOR]

2) Configure your outgoing mail server - in my case I have created a new file ~/.mutt/muttrc which contains just two lines:

[COLOR="SeaGreen"]**Not sure how to create a file, do I just type this into the console?**[/COLOR]

```
set smtp_url="smtp://my.smtp.server:25/"
set from="Me@My.Domain"
```



Replace my.smtp.server and [email]Me@My.Domain[/email] with your smtp server and your email address. Search for mutt and GMail etc if you use a different outgoing mail server.

[COLOR="SeaGreen"][B]Search for what in mutt and Gmail? Is "my.smtp.server" the one  my ISP has given me for emails that would be typed into say Thunderbird?
[/B][/COLOR]
3) Create the following script 

[COLOR="SeaGreen"]**How? Do I just type the below stuff into the console? How can I name it?**[/COLOR]

(I called it ip_monitor.sh), save it and make it executable:

[COLOR="SeaGreen"]**How do I make it "executable"?**[/COLOR]

```
#!/bin/bash
IPFILE=~/ipaddress
CURRENT_IP=$(wget -q -O - http://www.whatismyip.com/automation/n09230945.asp)
if [ -f $IPFILE ]; then
        KNOWN_IP=$(cat $IPFILE)
else
        KNOWN_IP=
fi
 
if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
        echo $CURRENT_IP > $IPFILE
        mutt -s "My IP is now "$CURRENT_IP me@my.domain < $IPFILE
fi
```

This script will create a file ~/ipaddress containing your IP address, obtained from whatismyip.com, and rewrite this file everytime your IP address changes.

It will send an email address with subject line and body containing the new IP address.

4) Add a cron entry (e.g. by crontab -e) to run this script 

[COLOR="SeaGreen"]**??? Is "cron" something like "task scheduler" but in code without GUI, like DOS?**[/COLOR]

at regular intervals, the line below would run it at 4:01 am every day:

```
01 4 * * * ~/ip_monitor.sh
```

Emails will only be generated if the IP address changed, not every time the cron job runs.

[COLOR="SeaGreen"][B]Thanks for posting this, I am sure it will be useful for other people who can use Linux but it looks like a day's work for me to even try... :cry:
Now if there were an app for people who write Linux to easily put a GUI to things, it would save man-years (millennia?) of key punching and multiply the user base x100... but that's a different thread.[/B][/COLOR]


...

---

### Post by CharlesA on 2009-10-08
> Following (various) instructions above, I have tried it with success according to the following steps:

1) Install Mutt. This is the only additional package you need.

[COLOR=SeaGreen]**I could possible do this if it's in "ADD AND REMOVE".**[/COLOR]

2) Configure your outgoing mail server - in my case I have created a new file ~/.mutt/muttrc which contains just two lines:

[COLOR=SeaGreen]**Not sure how to create a file, do I just type this into the console?**[/COLOR]

     Code:
     set smtp_url="smtp://my.smtp.server:25/"
set from="Me@My.Domain" 


Replace my.smtp.server and [EMAIL="Me@My.Domain"]Me@My.Domain[/EMAIL] with your smtp server and your email address. Search for mutt and GMail etc if you use a different outgoing mail server.

[COLOR=SeaGreen][B]Search for what in mutt and Gmail? Is "my.smtp.server" the one my ISP has given me for emails that would be typed into say Thunderbird?
[/B][/COLOR]
3) Create the following script 

[COLOR=SeaGreen]**How? Do I just type the below stuff into the console? How can I name it?**[/COLOR]

(I called it ip_monitor.sh), save it and make it executable:

[COLOR=SeaGreen]**How do I make it "executable"?**[/COLOR]

     Code:
     #!/bin/bash
IPFILE=~/ipaddress
CURRENT_IP=$(wget -q -O - [http://www.whatismyip.com/automation/n09230945.asp](http://www.whatismyip.com/automation/n09230945.asp))
if [ -f $IPFILE ]; then
        KNOWN_IP=$(cat $IPFILE)
else
        KNOWN_IP=
fi
 
if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
        echo $CURRENT_IP > $IPFILE
        mutt -s "My IP is now "$CURRENT_IP [EMAIL="me@my.domain"]me@my.domain[/EMAIL] < $IPFILE
fi 
This script will create a file ~/ipaddress containing your IP address, obtained from whatismyip.com, and rewrite this file everytime your IP address changes.

It will send an email address with subject line and body containing the new IP address.

4) Add a cron entry (e.g. by crontab -e) to run this script 

[COLOR=SeaGreen]**??? Is "cron" something like "task scheduler" but in code without GUI, like DOS?**[/COLOR]

at regular intervals, the line below would run it at 4:01 am every day:

     Code:
     01 4 * * * ~/ip_monitor.sh 
Emails will only be generated if the IP address changed, not every time the cron job runs.

[COLOR=SeaGreen][B]Thanks for posting this, I am sure it will be useful for other people who can use Linux but it looks like a day's work for me to even try... :cry:
Now if there were an app for people who write Linux to easily put a GUI to things, it would save man-years (millennia?) of key punching and multiply the user base x100... but that's a different thread.
[COLOR=Black]
[/COLOR][/B][COLOR=Black]You can install Mutt from the Synaptic Package Manager, just do a seach for "Mutt." 

As for the SMTP server, that's probably the same server that your ISP gave you and you use in Thunderbird. It should be something like "smtp.isp.net. You'd need to google something like this here: [http://www.scottro.net/qnd/qnd-gmail.html](http://www.scottro.net/qnd/qnd-gmail.html) it's kinda confusing tho.

You can copy and paste the script into text editor (gtext) then save it in your home directory after changing a couple things the email address it will send to.[/COLOR][/COLOR][COLOR=SeaGreen][COLOR=Black] 

You can make it executable by running chmod +x ip_monitor.sh from a terminal window.

Cron is like task scheduler, yes, but it does sorta have a GUI (kinda) run sudo crontab -e to edit the tasks listed there. Check here: [http://clickmojo.com/code/cron-tutorial.html](http://clickmojo.com/code/cron-tutorial.html) for some info on how to use it.

Hope this helps. :-)[/COLOR][/COLOR]

---

### Post by CharlesA on 2009-10-08
I did it a different way:

Installed exim4 and set it up to send via gmail: [http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)

I put this code into a file:

```

#!/bin/bash
# Checkip by t0p, based on a script by Dave at onthefencedevelopment.com
IPFILE=/home/***username***/ipaddress
CURRENT_IP=$(wget -q -O - http://www.whatismyip.com/automation/n09230945.asp)
if [ -f $IPFILE ]; then
        KNOWN_IP=$(cat $IPFILE)
else
        KNOWN_IP=
fi
 
if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
        echo $CURRENT_IP > $IPFILE
        cat $IPFILE | mail -s "IP has changed" ***user@example.com***
fi
```

Made it executable with chmod +x from the terminal screen.

Added it to cron with sudo crontab -e to edit. Same tutorial on how to use cron as above.

---

### Post by StuartN on 2009-10-08
> **MarkX said:**
> Thanks for posting this, I am sure it will be useful for other people who can use Linux but it looks like a day's work for me to even try...
Now if there were an app for people who write Linux to easily put a GUI to things, it would save man-years (millennia?) of key punching and multiply the user base x100... but that's a different thread.

One of the most attractive features of Linux is that it shields users so effectively from the intricacies of the GUI - 10 lines of code pasted from a forum and you're done.

---

### Post by MarkX on 2009-10-08
Check this out folks!!
(found on sourceforge)

[http://www.ip-monitor.com.ar/download.php](http://www.ip-monitor.com.ar/download.php)

It has Linux versions too.
You'll need 7zip to open the files.

I'm trying a windows version and it does detect the IP and send the email but in the received email I just get [NEW_IP_HERE]  instead of the actual IP.

This has a rather neat (perfect, in fact) GUI for everything.

Does it work in Ubuntu?

---

### Post by pupi1985 on 2009-10-08
Hi MarkX.

Thanks for the comment and the bug report.

> You'll need 7zip to open the files.There is no need of 7zip. Check the "Other releases" section in the [Download]("http://www.ip-monitor.com.ar/download.php") page.

> I'm trying a windows version and it does detect the IP and send the email but in the received email I just get [NEW_IP_HERE] instead of the actual IP.I've just added a comment on the [bug]("http://sourceforge.net/tracker/?func=detail&aid=2875141&group_id=204297&atid=989047") you've opened at SourceForge. 

> Does it work in Ubuntu? As it is Java based it should run under any OS with a JRE. I remember testing it under Ubuntu a year ago and a 64-bit Xubuntu.

Hope you find this info useful. ;-)

---

### Post by MarkX on 2009-10-09
Hello, author of IPmonitor, we are not worthy! :)

Just managed to read your reply and I did use test, I'll try what you suggested.
As you can see there are a few people who are interested in IP mailers. While there are scores of them for windows (and I'm sure some are noxious) yours is the only one I could find for Linux.
If yours can be made to work for the "add and remove" programs button in Ubuntu, then it should really be included in Ubuntu's repositories and I'll try to find a way to ask Canonical that it be added.

Would be good if others here could test it...

---

### Post by t0p on 2009-10-09
> **MarkX said:**
> That's all very Dandy for you Linux folk and I'm jolly glad it was so easy for you to get to work but how about something ordinary mortals can make sense of?:confused:

Since you've been a member of these forums sonce 2007, and have been asking ubuntu-related questions, I assumed you were also "Linux folk".  You use Linux, don't you?

> **MarkX said:**
> 
 I'm dumb and need a GUI.:cry:

I have no idea how dumb you may be.  But few people "need a GUI".

> **MarkX said:**
> 
Is there anyone who can turn this into something that can be downloaded and installed? With some Icon that tells people it's actually running? :(

I gave pretty specific instructions in my post.  Combined with other comments in this thread, there is everything you need to get the ipmonitor-emailer up and running on an Ubuntu system.  You don't need an icon to tell you it's running: follow the instructions and it will run whenever the computer is on.

If you have any specific questions, feel free to ask here.  Scroogle is also your friend.

**EDIT:** I just noticed your reply above to the author of IPMonitor.  I'm glad you've found the GUI you like to use.  Disregard my comments.

Or don't.  Maybe you can't be bothered to learn about scripts and Linux right now.  But it would be a good idea to do so.  One day.

---

### Post by StuartN on 2009-10-09
> **t0p said:**
> there is everything you need to get the ipmonitor-emailer up and running on an Ubuntu system.

And of course (which is why I was interested) once you have an automated email alert, you can add some additional lines to the script to attach the most recent webcam motion snapshot, the available disk space, a list of running processes and even current CPU temperature.

---

### Post by MarkX on 2009-10-10
Well, I tried IPmonitor in windows and it works like a charm.
I have no idea how to get it running in Linux ](*,) though, even after wasting an hour attempting to "execute .jar files". Getting fed up with Linux again. It's hugely labour intensive.

---

### Post by brian mcgee on 2009-10-10
> **MarkX said:**
> Well, I tried IPmonitor in windows and it works like a charm.
I have no idea how to get it running in Linux

Is Java installed? Can you post the output of the following command?

```
java -version
```

---

### Post by MarkX on 2009-10-11
> **brian mcgee said:**
> Is Java installed? Can you post the output of the following command?

```
java -version
```

java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Client VM (build 14.2-bo1, mixed mode, sharing)

---

### Post by MarkX on 2009-10-11
Never mind. I've given up with trying to get Linux to do anything more involved than word processing and internet browsing.
The point of the excercise was to set up a (secure) remote webcam surveillance system but there are no usable surveillance apps in Linux anyway. Zoneminder etc are just too ridiculously complicated to just install, never mind use, even if I can get a webcam working in Linux. Even remote desktop in Linux won't show the remote playing webcam vid on the one webcam I did get going after hours of fiddling.

I'm no fan of M$ but this sort of stuff is a matter of a few  clicks and no consoles in Windows.
Now looking at scheduled macros in XP.

---

### Post by StuartN on 2009-10-11
> **MarkX said:**
> Even remote desktop in Linux won't show the remote playing webcam vid on the one webcam I did get going after hours of fiddling.

Video on remote desktop?!

---

### Post by brian mcgee on 2009-10-12
> **MarkX said:**
> ...there are no usable surveillance apps in Linux anyway. Zoneminder etc are just too ridiculously complicated to just install, never mind use
You can install them from the repository pretty simply:
```
sudo apt-get install zoneminder
```Or, for Motion:
```
sudo apt-get install motion
```If you don't like the terminal, you can also install applications through Synaptic by going to System -> Administration -> Synaptic Package Manager. As for configuring, here are a couple of walkthroughs I found after a quick search:

[http://ubuntuforums.org/showthread.php?t=1050638](http://ubuntuforums.org/showthread.php?t=1050638)

[http://www.junauza.com/2009/07/turn-ordinary-webcam-into-security-spy.html](http://www.junauza.com/2009/07/turn-ordinary-webcam-into-security-spy.html)

---

### Post by mlinuxuser on 2009-10-18
> **MarkX said:**
> Hello folks!
I need a prog, preferably with GUI, which emails my dynamic IP to my email every time it changes (so I can access my security cams, for example or use remote desktop). There are numerous such IP mailer progs for windows but is there an equivalent one for Ubuntu please?

(I don't want to use dyndns. It closes free accounts if they are not used for a month and I don't want/need to rely on some other company!)

Sorry for interrupting the discussion. 

I am a beginer to networks related stuffs. I wish to know that, what are the benefits of  monitoring IP in general? Will It inform us what are the threats we are getting? or something else?

---

### Post by mlinuxuser on 2009-10-18
no responses yet??

---

### Post by brian mcgee on 2009-10-18
> **mlinuxuser said:**
> I wish to know that, what are the benefits of  monitoring IP in general? Will It inform us what are the threats we are getting? or something else?

In this case, I suspect everybody is interested in keeping tabs on their public IP address so they can access resources in their home network. For example, let's say I'm at work, but I forgot an important file at home. Knowing my home network's public IP address would be one requirement to grabbing that file. If you have other questions, they might have already been answered in the Networking section of the forums. If not, don't hesitate to open a thread! :)

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Also, I did a quick search and found this -- looks pretty comprehensive for an intro to networking:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch02_:_Introduction_to_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch02_:_Introduction_to_Networking)

---

### Post by Neezer on 2009-10-19
I am having a problem trying to run my script...I am pretty sure I did everything properly, but when I try to run Checkip, I get an error returned.

```

nate@server:~/bin$ Checkip
wget: invalid option -- '0'
/home/nate/bin/Checkip: line 5: [-f: command not found

```

I know my email will work though as I did a test send of an email to me, but this script doesn't seem to be working for me.

here is my code...I couldn't copy/paste, so I had to type it all out. I don't think there are any typos in it.

```

#!/bin/bash
# Checkip by t0p, based on script by Dave at onthefencedevelopment.com
IPFILE=/home/nate/ipaddress
CURRENT_IP=$(wget -q -0 - http://www.whatismyip.com/automation/n09230945.asp)
if [-f $IPFILE ]; then
       KNOWN_IP=$(cat $IPFILE)
ELSE
       KNOWN_IP=
fi

if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
       echo $CURRENT_IP > $IPFILE
       cat $IPFILE | mail -s "IP has changed" neezer96@gmail.com
fi


```


EDIT: just had to do some code debugging... changed a 0 (zero) to a O (capital letter o). Put a space on line five (from if [-f ....] to if [ -f ....])

Also had ELSE instead of else....case sensitive!!! I can run Checkip from terminal now and it emails me. when I run it from crontab, I get an error delivery message sent to my email....

This is what my message says a whole bunch of stuff...the crux of it is \

```


/bin/sh: /nate/bin/Checkip: not found


```

I think I need to recheck the path that I enter to my Checkip file....it is home/bin.....


changed /nate/bin/Checkip to ~/bin/Checkip....and that didn't work....now the message is 
```


/bin/sh: /root/bin/Checkip: not found

```

---

### Post by CharlesA on 2009-10-19
> **Neezer said:**
> I am having a problem trying to run my script...I am pretty sure I did everything properly, but when I try to run Checkip, I get an error returned.

```

nate@server:~/bin$ Checkip
wget: invalid option -- '0'
/home/nate/bin/Checkip: line 5: [-f: command not found

```

I know my email will work though as I did a test send of an email to me, but this script doesn't seem to be working for me.

here is my code...I couldn't copy/paste, so I had to type it all out. I don't think there are any typos in it.

```

#!/bin/bash
# Checkip by t0p, based on script by Dave at onthefencedevelopment.com
IPFILE=/home/nate/ipaddress
CURRENT_IP=$(wget -q -0 - http://www.whatismyip.com/automation/n09230945.asp)
**if [-f $IPFILE ]; then**
       KNOWN_IP=$(cat $IPFILE)
ELSE
       KNOWN_IP=
fi

if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
       echo $CURRENT_IP > $IPFILE
       cat $IPFILE | mail -s "IP has changed" neezer96@gmail.com
fi


```


EDIT: just had to do some code debugging... changed a 0 (zero) to a O (capital letter o). Put a space on line five (from if [-f ....] to if [ -f ....])

Also had ELSE instead of else....case sensitive!!! I can run Checkip from terminal now and it emails me. when I run it from crontab, I get an error delivery message sent to my email....

This is what my message says a whole bunch of stuff...the crux of it is \

```


/bin/sh: /nate/bin/Checkip: not found


```

I think I need to recheck the path that I enter to my Checkip file....it is home/bin.....

```
#!/bin/bash
# Checkip by t0p, based on a script by Dave at onthefencedevelopment.com
IPFILE=/home/username/ipaddress
CURRENT_IP=$(wget -q -O - http://www.whatismyip.com/automation/n09230945.asp)
**if [ -f $IPFILE ]; then**
        KNOWN_IP=$(cat $IPFILE)
else
        KNOWN_IP=
fi
 
if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
        echo $CURRENT_IP > $IPFILE
        cat $IPFILE | mail -s "IP has changed" user@example.com
fi
```

There is a space between -f and [, I don't know if it's a typo or not, but that's the only difference I see.

EDIT: D'oh! Just saw yer edit. Does it work now?

EDIT2: If you are using putty, you can open something like nano and right click to paste something. Ctrl + C to copy. :-)

---

### Post by Neezer on 2009-10-19
Thanks Charles!

I got the script working great, but now I am having issues with crontab....

and I think there is a problem with my exim4 setup.

In the email I get, I also get 
```

This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

    root@neezer.com

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 550 550 5.1.1 <root@neezer.com> recipient rejected (state 14).

  ----- Original message -----

Received: by 10.115.86.3 with SMTP id o3mr6269592wal.206.1255958703012;
       Mon, 19 Oct 2009 06:25:03 -0700 (PDT)
Return-Path: <neezer96@gmail.com>
Received: from server (c-75-71-165-69.hsd1.co.comcast.net [75.71.165.69])
       by mx.google.com with ESMTPS id 22sm171039pxi.6.2009.10.19.06.25.02
       (version=TLSv1/SSLv3 cipher=RC4-MD5);
       Mon, 19 Oct 2009 06:25:02 -0700 (PDT)
Received: from root by server with local (Exim 4.69)
       (envelope-from <root@neezer.com>)
       id 1MzsEP-0006uE-Tl
       for root@neezer.com; Mon, 19 Oct 2009 07:25:01 -0600
From: Cron Daemon <neezer96@gmail.com>
To: root@neezer.com
Subject: Cron <root@server> ~/bin/Checkip
Content-Type: text/plain; charset=UTF-8
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <E1MzsEP-0006uE-Tl@server>
Date: Mon, 19 Oct 2009 07:25:01 -0600

/bin/sh: /root/bin/Checkip: not found


  ----- End of message -----

```

At the bottom, I am pretty sure that error is just that I am not specifying the path to my Checkip file properly.

I have no idea what the top part is saying. I think it is really weird that I can run Checkip from the command line in putty and get an email with my ip address in it, but when crontab calls Checkip I get an error message about my email server...


**EDIT:**
SUCCESS!!!!

I changed the path in crontab to * * * * * /home/nate/bin/Checkip
set to every minute to debug


seems to do the trick. I can change the ip address in the file ipaddress and then I get an email telling me that it has changed. The script only sends an email if the ip address in the file has changed though, so should be good to go!

thanks for the help and the links. I had some problems with one of the exim4 setup sites, but this one worked for me.
[http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)

The other one, [http://wiki.debian.org/GmailAndExim4](http://wiki.debian.org/GmailAndExim4) gave me problems...when I ran: ```

# update-exim4.conf

```

nothing happened, and I tried going through the problems section, but didn't make any headway. 


So I did make a /etc/exim4/passwd.client file. I don't know if you absolutely need this file because the other tutorial doesn't have you make that file at all.

I hope this information helps anyone who is trying to get this working.

I know it will help when my isp changes my ip address and I'm away from home. Looks to me like they change it weekly, but I have it running a check hourly at the moment.

---

### Post by CharlesA on 2009-10-19
It means that there was no recipient listed for [email]root@neezer.com[/email].

there is a /root folder on my server, but it's DWRX root only.

Maybe do what I do and keep the script file in your home folder, so you don't have to deal with permissions?

I've got mine here:

/home/charles/checkip

Cron job looks like this:

# Check external IP and email if changes
0 */3 * * * ~/checkip >/dev/null 2>&1

From my limited experience, it looks like your mail server isn't configured correctly. 

How did you set it up to use gmail?

EDIT: Is the checkip file named Checkip or checkip? Linux is case sensitive (but you know that already :-P)

Also, in my server the /root folder is empty. Maybe that's the problem?

---

### Post by StuartN on 2009-10-20
Having run this for a couple of weeks, I realize that the /var/mail/me file is a great historical record - so long as the elements can be extracted.

Writing the email with <ip_address>current_ip</ip_address>, <lm_sensors>sensors_output</lm_sensors>, <disc_use>du_output</disc_use> would give you a file where you can separate a dated list of all the individual items in a status report.

So every time the IP address changes, you would run sensors, either du -s /home or df and anything else you might want to know about your remote PC's health.

To see a list of one of these items you could:

```
 sed -n '/<disc_use>/,/<\/disc_use>/p' /var/mail/me
```

and sed will strip the mailfile me of everything except the disc use output. Extract the message dates as well and you can graph it - use <date>output of date +%Y/%m/%d</date> in the status email.

---

### Post by Neezer on 2009-12-21
Well, I'm having problems setting up exim4 in 9.10...

I am getting a strange error when I try to update the file

```

nathan@server:~$ sudo update-exim4.conf
[sudo] password for nathan: 
2009-12-21 21:58:46 Exim configuration error:
  two client authenticators (gmail_login and login) have the same public name (LOGIN)
Invalid new configfile /var/lib/exim4/config.autogenerated.tmp, not installing 
/var/lib/exim4/config.autogenerated.tmp to /var/lib/exim4/config.autogenerated


```

I have no idea how to find the extra client authenticator...

---

