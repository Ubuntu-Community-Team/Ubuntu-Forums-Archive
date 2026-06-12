---
title: "Upstart fails to start a Perl script"
date: 2011-01-22
forum: General Help
---

### Post by noh.way.jose on 2011-01-22
[FONT="Arial"]On Maverick + up-to-date on updates on Mini ITX (Asus AT3N7A-I)[/FONT]

[FONT="Arial"]I have a Perl script that I want to run continually to extract values from XML that appears on a USB port every 5 seconds and stuff the extracted values into an RR Database (RRD). I have created an Upstart job, called currentCost.conf (permissions=644 owner=root):
[/FONT]
[FONT="Courier New"]
#readCurrentCostData4RRD.pl daemon

description "regular background program processing daemon"

start on runlevel [5]
stop on runlevel [!5]

expect fork
respawn

exec perl /home/greg/currentCost/readCurrentCostData4RRD.pl > /tmp/RCCD4RRD.out 2>&1[/FONT]


[FONT="Arial"]The Perl script is called readCurrentCostData4RRD.pl  (permissions=755 owner=me):[/FONT]

[FONT="Courier New"]#!/usr/bin/perl -w

# Reads data from a Current Cost device via serial port.

use strict;
use Device::SerialPort qw( :PARAM :STAT 0.07 );

#serial-----------------
#my $PORT = "/dev/ttyS0";

#USB----------------- 
my $PORT = "/dev/ttyUSB0";
my $ob = Device::SerialPort->new($PORT);

#serial------------
#$ob->baudrate(9600);

#USB----------------baud 9600 recommended as is 57600
$ob->baudrate(9600);
$ob->write_settings;

open(SERIAL, "+>$PORT");
while (my $line = <SERIAL>) {
if ($line =~ m!<ch1><watts>0*(\d+)</watts></ch1>.*<tmpr> *([\-\d.]+)</tmpr>!) {
my $watts = $1;
my $temp = $2;

my $stdout = `rrdtool update /home/greg/currentCost/powertemp.rrd N:$watts:$temp`;
# print "$stdout\n";
# print "$watts Watts, $temp deg C\n";
}
}
[/FONT]

[FONT="Arial"]I can start the Perl process with [FONT="Courier New"]sudo start currentCost[/FONT] but it just doesn't happen automatically when I reboot.

Can anyone see a schoolboy error? I got the impression from a post elsewhere that environment variables may play a part but I couldn't see how, in this case?

Cheers,

Greg[/FONT]

---

### Post by gmargo on 2011-01-22
"They" don't really use run levels with as fine a granularity anymore like in the old days.

Grep through the other files in /etc/init/ and you'll see the majority say "start on runlevel [2345]".  Give that a try.  The **runlevel(8)** command tells me that my machine is running now at level 2, even though it is fully multiuser with a windowing system running.

Also, I think your open statement should open for reading only and check the return code.
```

open(SERIAL, "<", $PORT) || die("Cannot open $PORT: $!");

```Note also that the "while ($line = <SERIAL>)" command will wait until a newline is received.  If your device is sending XML without intervening newlines, then you have to make different arrangements.

---

### Post by hawkmage on 2011-01-22
Try using the fully qualified path to the perl executable.  Quite often with start up scripts and cron jobs the path varable is either not set or is very limited.

---

