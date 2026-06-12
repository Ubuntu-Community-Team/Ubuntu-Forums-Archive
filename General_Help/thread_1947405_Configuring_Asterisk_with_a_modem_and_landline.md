---
title: "Configuring Asterisk with a modem and landline"
date: 2012-03-26
forum: General Help
---

### Post by Kissell on 2012-03-26
I have a computer running XBMC in Ubuntu, and XBMC has a plugin which allows it to connect to an open-source Asterisk PBX.  

My goal here, is to get XBMC to display incoming caller ID on the landline.

I've put a PCI modem in the computer and connected the landline and installed asterisk...  

But I don't know how to configure asterisk with an regular modem.  Most stuff I'm coming across on google refers to using special PBX cards or SIP for VoIP...  but I'm trying to do this with a regular modem and a landline.

---

### Post by jonobr on 2012-03-26
Hello


Connecting the modem into the phone line wont work.
The PCI modem is for modulating and demodulating data to/from the analog line

In order to connect an incoming line to the asterisk PBX you would need an FXO card that asterisk would support. FXO [Here]("http://www.x100p.com/products/FXO.php")
is one fxo example, there are others out there which offer more then one port.



Cheers

jonobr

---

### Post by Kissell on 2012-03-26
Okay...  "It can't be done" isn't the answer I wanted..  but I guess buying an FXO card isn't that big of a deal..  

I just had a modem laying around and thought certainly that would work, since I don't need a full PBX, I just want XBMC to display caller ID information, and I know a modem can get that information.

---

### Post by jonobr on 2012-03-26
ok,

So let me reverse course a bit here.

My thinking was you wanted to use it as a voip endpoint, but I understand now you want to use it just to see the CID information coming in.
That means an FXO card is probably way overkill, but work is required.

A modem will most definitely see a CID if it is presented
I never have seen a way of getting any CID stuff from a modem into asterisk,  but reading around mgetty may be able to get what you need. However, the trick with this is getting the info and then using that info


Im posting info from a site I don't want to direct you to,
but you could probably find,
The interesting thing in my defense, the respondent in this used the words to the OP "you need an FXO module"
It was like dejavue all over again.......

> 

Possible CID logging in Linux with mgetty

I have found that mgetty is capable of capturing CID from supported modems. Any Hayes compatible modem with Linux drivers that offers CID should be able to work with mgetty for this task. There is a configuration file for mgetty (/etc/mgetty-sendfax/mgetty.conf by default) that contains the cnd-program definition. When this is set and an incoming call is detected, the specified program will be called with the following commandline arguments:
<tty> <CallerID> <Name> <dist-ring-nr.> <Called Nr.>

A real simple Perl script to be called as the cnd-program that dumps the arguments in to a tab delineated file completes the logger.

Because mgetty is supposed to use the cnd-program to selectively block/allow incoming calls, the return value of the script determines if the call should be answered or dropped. Simply exiting the script with a return value of 1 will disconnect each call once logged.




Again, its one thing getting the CID info through logging however, putting that into XBMC... thats something else!

---

### Post by Kissell on 2012-03-26
Well, the XBMC application is the main program for this machine to exist, and it is full-screened the entire time as a home theater PC.  XBMC interfaces easily with Asterisk, but I haven't seen anything for mgetty, so that's my driving reason for looking into Asterisk, because it can easily display the caller ID in the XBMC application and do things like pause video playback and maybe even voice announce the caller.

I have a programming and IP networking background, but have always managed to not get too involved with the PBX or VoIP stuff...  I guess now is as good a time as any to mess with it.  Having a full featured PBX that handles VoIP and does everything I could possibly imagine but would never use, is certainly overkill...  but I've got those toys already in everything else, might as well get that toy for the phone too.  In addition to caller ID I would like to automatically send calls to voicemail based on time of day and e-mail those voicemails as mp3 files, as I get a bunch of calls at inappropriate hours.  And out-right reject or block calls from certain places, like the Jamacian Prince who keeps calling, and unavailable, unknown, or private numbers.  And I'm sure in the future I'd like to receive SIP and Skype and Google Voice calls and handle them...  

Found a FXO card on ebay for $25 after shipping...  only one port for the PTSN, but I only have one landline.  Might as well start playing...  although asterisk looks complicated, in that there seems to be very little intuitive flow about it for a newbie.  It just installs, and that's it...  it's running...  no GUI, no text config menu, no information about where the files are to configure it, or how to configure it...  just installed and done...

---

### Post by jonobr on 2012-03-26
Hi

If you have the available hardware and the time, 

I would recommend strongly using [Pbx in a flash (Piaf)]("http://pbxinaflash.net/") or 
incredible or one of those derivatives.


I would recommend Piaf as its well documented (look for piaf without tears) based on asterisk.

It installs everything including the OS, so hopefully the machine is one sitting in the corner and can be wiped.

Im pretty sure it will do all you need via the admin gui and doesn't require you knowing all the config files and CLI.

Lastly, your eagerness to learn is fantastic,
My hats off to you

---

### Post by Kissell on 2012-03-26
Thanks for sharing PIAF, Incredible PBX looks great, other than it's an ISO install....  

I'd really like to stick with Ubuntu and not reformat as I've got this machine also running some custom daemons I've written, and I want it to still be cable to run XBMC in a 1920x1080 resolution...  not sure if I'll be able to get PIAF's OS to do that.  Too many maybes to blow away the machine and start over...  

I guess I'll try to do Asterisk the hard way, and if I get too frustrated I'll download the Incredible PBX ISO image and try running it in a VM.

---

### Post by Kissell on 2012-03-30
Well, the FXO card arrived and I installed it...  but I'm still not sure how to configure asterisk to use it.

---

