---
title: "Adding Thunderbird Prefered Application"
date: 2010-02-22
forum: General Help
---

### Post by sandman3838 on 2010-02-22
Hello

I have Ubuntu 9.10 64but with Mozilla Thunderbird (Shredder v3.0.3pre) and Firefox 3.5.8.

I can't seem to get the Menu - File - Send Link to work nothing happens.
Also for Preferred Applications the only thing available for the Mail Reader is the choice custom.  I removed Evolution earlier.

I suspect that if I populate the Mail Reader with the proper command line it should fix my problem.

Would you mind letting know what your command line is?

---

### Post by wojox on 2010-02-22
Have you rebooted since you installed TB3? Try that and it should show up in preferred applications..

---

### Post by sandman3838 on 2010-02-22
Thanks for the help....

Yes I did reboot the system.  It's still a bust!

Now its' gotten worse the link to this thread that I received in an Email asked me what program I wanted to open it with.

I seriously thinking about using Sympathetic and doming a complete removal of both and then re-installing.

---

### Post by sandman3838 on 2010-02-22
Ok  This worked for me.

**(NO IT DIDN'T MY FAULT!  WITH THE COMMAND LINE BELOW IS OPENS JUST THUNDERBIRD NOT A THUNDERBIRD OPEN LINK TO SEND A LETTER)**

I did you looking around and this solved my issue.

1. Through Synaptic I removed Friefox & Thunderbird. After I backup my data.

2.  I found this:  

**** INSTALL FROM STABLE PPA

1. To install from PPA, add the mozilla-daily PPA in the repository list.

    sudo add-apt-repository ppa:mozillateam/firefox-stable

2. Update the software list using the command

    sudo apt-get update

3. Install Firefox 3.6 using the command

    sudo apt-get install firefox-3.6

As for Thunderbird I can't remember the script for that one?  Sorry!

Then.......

To get Firefox to open a compose window via the &#8220;Send Link&#8221; option, do this:

   1. Open firefox and in the address bar, type &#8220;about:config&#8221;

   2. Right-click within the body of the page that opens and select &#8220;New&#8221; and then &#8220;String&#8221;

   3. In the dialog box, where it says &#8220;Enter preference name&#8221;, paste: network.protocol-handler.app.mailto

   4. In the next dialog box, enter your path to Thunderbird. Mine is /usr/bin/thunderbird-3.0

   5. Hit OK and restart Firefox. &#8220;Send Link&#8221; should now work with Thunderbird.

Finally I added /usr/bin/thunderbird-3.0

For Custom under Mail in Preferred applications.

Reboot the system.


ANY SUGGESTIONS ANYONE?

Now Thunderbird is in preferred applications and seems to be working, does any one have any idea as to what the command line for the SEND LINK should be?

---

### Post by sandman3838 on 2010-02-22
OK with what I just added/installed I was hit with an update for Firefox....

Fixed?

---

