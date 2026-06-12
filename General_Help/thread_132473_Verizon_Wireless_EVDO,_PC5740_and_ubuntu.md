---
title: "Verizon Wireless EVDO, PC5740 and ubuntu"
date: 2006-02-18
forum: General Help
---

### Post by kelloggsx on 2006-02-18
I am new to ubuntu and I love to convert my winxp laptop to ubuntu, but before i even get going with the installation, I need to know if someone out there has actually made the Verizon Wireless EVDO, PC5740 to work on ubuntu.

I found an old post with some instructions on how to, but i am not sure if the guy actually got it working

here is the link:  kenkinder.com/evdo-pc5740/

Any suggestions?

---

### Post by skwid on 2006-02-18
Good luck on that one dude....

I'll keep an eye out.

---

### Post by fate on 2006-04-08
Hey there.

I'm currently using the PC5740 under Ubuntu Dapper Drake Flight 6 (AMD64 version). Ken uses it under Ubuntu 5.10. There is a small difference on my machine, but it should be pretty trivial: I'm using a PCI to PCMCIA adapter that allows me to use this wireless card on my desktop. It took a little doing, even using the instructions provided on Ken's webpage. I had the card already plugged in at the time of the install, and Ubuntu appeared to recognize it flawlessly.

Anyway, while Ken's configuration scripts came close, I had to do a little more research and found some other script examples that helped me a little better. Forgive me, whoever wrote these -- I didn't bookmark your webpage, but thanks. :)

I had to edit the scripts regardless, but here's what I came up with:

The **/etc/ppp/peers/1xevdo** file:

> ttyACM0

115200

debug

noauth

defaultroute

usepeerdns

connect-delay 10000

user [email]ENTERYOURVERIZONPHONENUMBERHERE@vzw3g.com[/email]

show-password

crtscts

lock

lcp-echo-failure 4

lcp-echo-interval 65535

connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/1xevdo_chat'

And the **/etc/ppp/peers/1xevdo_chat** file:

> ABORT 'NO CARRIER' ABORT 'ERROR' ABORT 'NO DIALTONE' ABORT 'BUSY' ABORT 'NO ANSWER' '' 
'ATZ' ATZ 'AT' AT 
ATDT#777 
TIMEOUT 70
CONNECT \d\c

As you can see, the 1xevdo_chat file is heavily edited from the Ken website -- his file didn't work at all. I tried my best to edit the script settings and whatnot, but it died with a 'fail' everytime.

I don't know whether I needed to do it or not considering the machine had already detected it, but I did it anyway: I entered **modprobe usbserial vendor= product=** etc. etc. upon finding out the vendor ID and product ID. You can find these out (if you've installed Dapper with the card already inserted) under System -> Administration -> Device Manager in Gnome. Look at the advanced tab of the device -- it was called Curitel Communcations for me.

Anyway, hope this helps.

One note: Web pages load, but I can't get Synaptic to recognize it's connected to the internet. I'm a little bumfuzzled there.

See you.

---

### Post by jdseek on 2006-07-27
With 6.06, it is possible to verify your connectivty with your PC5740 with the liveCD.  The same process that gets you internet in the liveCD will get you going in a full install.  I can't say how fast this way is as opposed to the other ways.  But I can say I spent many frustrated nights banging on the keyboard before I stumbled on this idea. It fixed my problems in less than 10 minutes.
Information here is based on what I learned from [http://kenkinder.com/evdo-pc5740/]("http://kenkinder.com/evdo-pc5740/")

Assuming you have ubuntu 6.06 running, (installation or liveCD for testing)

Step One BEFORE YOU INSERT THE CARD!
This verifies your vendor and product codes

```
you@yourbox:~$ cat /proc/bus/usb/devices > devices
```

Insert the card now.

Then

```
you@yourbox:~$ diff /proc/bus/usb/devices devices  | grep Vendor
< P:  Vendor=0000 ProdID=0000 Rev= 2.06
< P:  Vendor=0000 ProdID=0000 Rev= 2.06
< P:  Vendor=106c ProdID=3701 Rev=0.00
```

In my case the vendor code is 106c and the product ID is 3701
If your numbers are different, replace these with yours in the next step.

The next step may not be nessicary, but we will do it anyway to make sure.
Hey, it worked for me.

```
you@yourbox:~$ sudo modprobe usbserial vendor=0x106c product=0x3701
```

Now check for your new device by typing:

```
you@yourbox:~$ ls /dev/ttyACM0
/dev/ttyACM0
```

If you get an error, such as
```
you@yourbox:~$ ls: /dev/ttyACM0
ls: /dev/ttyACM0: No such file or directory
```
post it here, along with the output of 
```
you@yourbox:~$ dmesg
```

If no errors then lets go configure that thing to get online!

Next we must write (or modify) the wvdial configuration, first make a backup of your old one

```
you@yourbox:~$ sudo cp /etc/wvdial.conf /etc/wvdial.conf.backup
```
then we start the editor by
```
you@yourbox:~$ sudo nano -w /etc/wvdial.conf
```

Copy and paste this into the file
[B]IMPORTANT!
MAKE SURE YOU REPLACE *<your-phone-number-here>*with your access card's phone number![/B]

```
[Dialer Defaults]
Stupid Mode = on
Modem = /dev/ttyACM0
Baud = 921600
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777
Username = ***<your-phone-number-here>***@vzw3g.com
Password = vzw
Init1 = ATZ
ISDN = 0
Modem Type = Analog Modem
Auto Reconnect = on
Carrier Check = no

[Dialer shh]
Init3 = ATM0

[Dialer pulse]
Dial Command = ATDP

```

then save your work and exit by
```
<ctrl+x>
y
<enter>
```


Now we're ready to try our new connection out.

```
you@yourbox:~$ sudo wvdial
```

[note:install only, it may ask for a password, enter it to continue]

If that gets you going, but you drop the connection alot, try this, if not, I say, if it ain't broke, don't fix it.

_**Warning, the next step still needs some tweaking.**_ I used this to avoid dropping the connection while updating.

```
you@yourbox:~$ sudo cp /etc/ppp/peers/wvdial /etc/ppp/peers/wvdial.backup
you@yourbox:~$ sudo nano -w /etc/ppp/peers/wvdial

```

copy and paste these 2 lines onto the end of the file

```
lcp-echo-failure 65535
lcp-echo-interval 65535
```

Good luck and happy interneting.  I really enjoy my access card now that it works in ubuntu.

Good luck, JD

---

### Post by rick_1010 on 2006-10-12
This is an alternate method that has been working well for me for a while. It is from: [http://www.linux.com/article.pl?sid=06/03/08/2138237](http://www.linux.com/article.pl?sid=06/03/08/2138237)

(If you have any problems with it on Ubuntu, post here and I will help as I have went through this over and over and can probably figure what the problem is)

-----------------
First, determine the product and vendor number of your EVDO card so you can call the correct kernel modules. If you're using the PC5740, I'll save you a few steps and tell you the numbers; write them down because you'll need them in the following step:

vendor=0x106c product=0x3701

If you're using another EVDO card, before you insert it, open a terminal window and type the following command as root:

cat /proc/bus/usb/devices devices

Then insert the card and type this command as root:

diff /proc/bus/usb/devices devices | grep Vendor

Your vendor and product numbers should come up in this format:

< P: Vendor=106c ProdID=3701
Rev=0.00

Now it's time to add the proper kernel module to include support for your card. Linux sees EVDO cards as USB/serial modems, so issue this command, again as root, inserting the correct numbers for your card:

modprobe usbserial vendor=0x106c product=0x3701

To verify that things are going as they should, change to the /dev directory and list the files there. You should see a file called ttyACM0; this is the name the computer has given your card.

You can use several different programs to make the device ttyACM0 dial out in Linux, but I'll show you how to use pppd because most Linux distributions include it. You could type the necessary pppd commands every time you want to get online, but it's easier to create a simple script. You'll need to know your Verizon-issued 10-digit number because it acts as your username. All the other data is common to all Verizon wireless broadband accounts.

To write the script, open your favorite text editor as root and type the following, replacing xxxxxxxxx with your number:

ttyACM0
115200
debug
noauth
defaultroute
usepeerdns
connect-delay 10000
user [email]xxxxxxxxxx@vzw3g.com[/email]
show-password
crtscts
lock
lcp-echo-failure 4
lcp-echo-interval 65535
connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/1xevdo_chat'

Name the file 1xevdo and save it in /etc/ppp/peers/. Check out kenkinder.com for a detailed explanation of what some of these script line items are for.

The last line of the script calls another file that you need to create, called 1evdo_chat. Again, as root in your text editor, create a file that contains the following information:

ABORT 'NO CARRIER' ABORT 'ERROR' ABORT 'NO DIALTONE' ABORT
'BUSY' ABORT 'NO ANSWER'
'' ATZ
OK-AT-OK ATDT#777
CONNECT \d\c

Name it 1xevdo_chat and save it in /etc/ppp/peers. This file contains modem commands, including the number 777, which it needs to dial to reach the Verizon EVDO network.

With your EVDO card plugged in, open pppd and call the scripts you just created. In a terminal as a regular user, type pppd call 1xevdo and press Enter. This command doesn't give you any immediate feedback, but you need to see what IP address Verizon assigns your modem, so type this command:

tail -f /var/log/messages

You should see a series of messages in your terminal similar to this:

Feb 15 20:12:48 localhost chat[7946]: abort on (BUSY)
Feb 15 20:12:48 localhost chat[7946]: abort on (NO ANSWER)
Feb 15 20:12:48 localhost chat[7946]: send (ATZ^M)
Feb 15 20:12:48 localhost chat[7946]: expect (OK)
Feb 15 20:12:48 localhost chat[7946]: ATZ^M^M
Feb 15 20:12:48 localhost chat[7946]: OK
Feb 15 20:12:48 localhost chat[7946]: -- got it
Feb 15 20:12:48 localhost chat[7946]: send (ATDT#777^M)
Feb 15 20:12:48 localhost chat[7946]: expect (CONNECT)
Feb 15 20:12:48 localhost chat[7946]: ^M
Feb 15 20:12:50 localhost chat[7946]: ATDT#777^M^M
Feb 15 20:12:50 localhost chat[7946]: CONNECT
Feb 15 20:12:50 localhost chat[7946]: -- got it
Feb 15 20:12:50 localhost chat[7946]: send (\d)
Feb 15 20:12:51 localhost pppd[7945]: Serial connection established.
Feb 15 20:12:51 localhost pppd[7945]: Using interface ppp0
Feb 15 20:12:51 localhost pppd[7945]: Connect: ppp0 /dev/ttyACM0
Feb 15 20:13:01 localhost pppd[7945]: local IP address 70.197.15.21
Feb 15 20:13:01 localhost pppd[7945]: remote IP address 66.174.38.5
Feb 15 20:13:01 localhost pppd[7945]: primary DNS address 66.174.95.44
Feb 15 20:13:01 localhost pppd[7945]: secondary DNS address 66.174.92.14

If the modem doesn't connect or gets disconnected, try again. Exit from pppd by holding down Ctrl-C. If you try to reconnect and you get this message:

Device ttyACM0 is locked by pid 6396

then become root, go to /var/lock, and delete the file that's locking ttyACM0. Type rm filename and press Enter.

Once you're connected successfully, you need to take one more step before you can surf. Look at your terminal message and find the local IP address that Verizon assigned to your card. Then, as root, open another terminal and type the following, inserting your IP address in place of the xxx.xxx.xxx.xxx:

route add default gw xxx.xxx.xxx.xxx

This command adds the local IP address to your routing table so your computer can communicate with other computers on the Internet. Now you should be ready to surf the Web, check your email, and connect to Internet Relay Chat with your Verizon EVDO subscription and Linux.

---

### Post by gilsoncav on 2006-10-14
Very nice Tip!
  I used the instructions to make a succesful connection with the mobile operator from Brazil (VIVO mobile) using a PCMCIA card from YISO, model c893. It worked perfect!
  Question: is there a workaround for the command **route add default gw xxx.xxx.xxx.xxx**?
   would like to be more agile to connect using just a command (pppd call 1xevdo).

thanks!!

Gilson Cavalcanti

---

### Post by scottvan on 2007-03-22
Thank you so much for helping me get the Verizon card working with Ubuntu.  One problem I've noticed, is testing the speed with [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

These are the results I get:

Ubuntu
164 kbps download
103 kbps upload

WindowsXP
560 kbps download
88 kbps upload

I have tried the tests several times and get the same results.  Anyone know why the download speed in Ubuntu is so much slower than in XP?  Or have I failed to tweak something correctly?

---

### Post by javatoast on 2007-04-04
I will echo that issue. The download speed is really bad. Would an adjustment to the baud rate in the script do the trick?

---

### Post by ryan8403 on 2007-04-10
When you're in windows are you using the VZ software to connect? I believe the last time that I used my phone in Windows the VZ software had some type of "accelerator" as part of the software which could explain the difference since ubuntu wouldn't have that.

---

### Post by loxety on 2007-06-20
Here is a link to the instructions I used to get the pc5740 working on 6.06 [http://ubuntuforums.org/showthread.php?t=336695&highlight=5740](http://ubuntuforums.org/showthread.php?t=336695&highlight=5740)

I also only see around 160kbps download speeds (x-RTT?).  I'm wondering how 7.04 would fair.  Still tinkering :popcorn:

---

### Post by jawrat on 2007-07-04
I just followed the directions in the post above (Having done this successfully two months ago as well), and i'm seeing speeds of 968/120 on my VZW evdo pc5740 card.  I think the speeds may also have to do with your local cell network and how busy/crowded it is.  I'm just happy it works.  

Thanks for the tutorial up there... ;)

---

### Post by timcredible on 2007-10-31
the slow speeds may be due to some settings.  you might want to check my how-to on setting up verizon broadband wireless cards, i ran into some slow speeds until i changed some things.
[http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=19&Itemid=27](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=19&Itemid=27)

---

### Post by okdok on 2007-11-03
Hi List-

I've been knocking my head on this one for a few days and hope someone can help. 

Here's the skinny-

I'm using an HP Compaq with a built-in wireless module: Sierra Wireless MC5720 (Verizon)
All tests were performed on clean installations of Ubuntu 7.10

First test I was dual booting with Windoze until I could get the EVDO card to connect.  I used the link timcredible posted above using gnome-ppp to connect.  It worked!  So I formatted the entire notebook for a new clean install of Ubuntu 7.10 w/out Windoze.

Unfortunately, after mirroring my steps the connection fails and returns the error NO CARRIER.  I confirmed that the card was recognized and would initialize. I also carefully reviewed my steps/commands without luck.

So, I attempted to use the earlier post in this thread by jdseek using wvdial.

Here is my wvdial.conf without the phone number for security.

```
[Dialer Defaults]
Stupid Mode = on
Modem = /dev/ttyUSB0
Baud = 921600
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D1 +FCLASS=0
Phone = #777
Username = **********@vzw3g.com
Password = vzw
Init1 = ATZ
ISDN = 0
Modem Type = Analog Mode
Auto Reconnect = on
Carrier Check = no

[Dialer shh]
Init3 = ATM0

[Dialer Pulse]
Dial Command = ATDP
```

Now here is what happens:

```
emateja@packet-mobile:~$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D1 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D1 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT#777
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT#777
WvDial Modem<*1>: NO CARRIER
```


](*,) It kills me becuase I was able to get this to work with my first test.  I can communicate with the card using minicom and it reports to be on and in range. I even wiped the drive again and returned to a dual boot environment using Windoze and can successfully connect using the card.  I just can't repeat my success in Ubuntu.

Thanks in advance for any help!

---

### Post by jawrat on 2008-05-13
well, hardy heron went and screwed the pooch on my verizon card (see previous post in this thread).  has anyone had any experience getting the 5740 to work with the heron?  please help!

---

### Post by okdok on 2008-05-14
Updated: Working!

Currently running Hardy 8.04. Out of the box, configured wvdial and it worked on both Verizon 5750 and Sprint Pantech PX-500 by running the following:

```

sudo wvdialconf

```

Then I modified the wvdial.conf accordingly:

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
Modem Type = USB Modem
ISDN = 0
New PPPD = yes
Phone = #777
Modem = /dev/ttyACM0
Username = ''
Carrier Check = no
Password = ''
Baud = 460800

```

Where I went wrong before was the username and password. These PPP connections do not require a username and password. Also, running the configuration command above helped detect the card properly.

Hope this helps someone. I'm loving Hardy!:)

Specs:

HP Compaq nc6400
Intel CoreDuo T2600
ATI X1300 using Restricted Driver

---

### Post by jawrat on 2008-05-14
thanks for your reply above!  I was able to get it working following your instructions above.  I didn't take long to test it, but it seemed like it was dropping the connection when it went idle for more than a minute or so...i'll do more testing and let you know.

---

### Post by okdok on 2008-05-15
Glad to have helped.

I have tested both the Verizon 5750 and Sprint Pantech PX-500 running all day without dropping. That is, on Hardy 8.04 using wvdial.

I do recall when trying the different hardware devices in Gutsy that I would occasionally drop the connection. I suggest two possible changes in:

```
/etc/ppp/options
```

Forgive me if I am wrong, I forgot to document. I would start by increasing the interval in the line reading:

```
lcp-echo-failure 4
```

If the connection is slow, I think that maybe ppp is quiting. Otherwise, if it is the carrier dropping the connection, try decreasing the other interval on the line reading:

```
lcp-echo-interval 30
```

Last, I saw a line further down that read:

```
#persist
```

If you can not keep the connection alive, then ppp will restart if you uncomment this line. Let us know how it goes. :-\"

---

### Post by Mordikar on 2008-05-17
I happen to work for VZW in the network support dept. There are drivers and a "vzaccess manager" for linux. Almost no one in tech support knows it exists as it's a fairly new project.

The software supports
SUSE 10.3
Fedora Core 8
Redhat Enterprise 5
and Ubuntu 7.10

not all the latest and greatest but it's better than nothing and a LOT easier than running specialty scripts and having to have windows installed as i've seen on some suggestions for getting our cards to work in linux. I have noticed though that sometimes if there is a pre-instaled airprime driver it starts causing conflicts. Fedora breaks the driver just about every time they release a new kernel.

---

### Post by Mach1US on 2008-05-19
I have had my card working back in 2006 and since ,all of other models have been working perfectly , in fact i'm posting this using vzw PC5750 , i have made this how-to if you still having problems.
My connection is most of the time over a Meg.
[http://ubuntuforums.org/showpost.php?p=2849062&postcount=14](http://ubuntuforums.org/showpost.php?p=2849062&postcount=14)

[http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo](http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo)

---

