---
title: "Firewall issue maybe stopping me browsing?"
date: 2011-03-03
forum: General Help
---

### Post by lonewolf88 on 2011-03-03
(Third attempt to post this - no idea where the others have gone - apologies if they turn up!)

10.04 Gnome, Toshiba T110 laptop

I can get connections to internet via ethernet and wireless, however cannot browse, ger mail, ping, etc etc.

These programs just don't recognise that I am connected.  Work ok in Win & Pro.

I must admit late last night I was fiddling with Guardog, then uninstalled same;  I feel I may have changed a firewall setting somewhere.

Of course Guardog no longer available as I have dumped it :(

What I would like is some assistance - maybe some command lines that can sort out & fix the issue?

And, as usual, Thanks in Advance!

(And I hope this post make it through!)

---

### Post by seawolf167 on 2011-03-03
Run

```
sudo iptables -L
```

to see if there are any firewall rules in place

---

### Post by lonewolf88 on 2011-03-03
> **seawolf167 said:**
> Run

```
sudo iptables -L
```to see if there are any firewall rules in place

Thanks for the quick reply.

Everything looks normal to an untrained eye - "accept" is the common word there - even has the isp of the hotel network that I am connected to at present (err .. is this normal BTW?)

Any other things I could try?

(BTW cannot copy the output as I have to log out & post through Windows, which works ok on this dual boot laptop).

---

### Post by seawolf167 on 2011-03-03
You can write the output to a file then transfer or email that to yourself, i.e.

```
sudo iptables -L > ~/Desktop/iptables.txt
```which will output to the file "iptables.txt" on your desktop

Your iptables with no rules in place should look like this:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```You might want to reinstall guarddog

```
sudo apt-get install guarddog
```run it with su privileges

```
gksudo guarddog
```make sure everything is turned off and reset to default settings, then completely remove the program and its config files

```
sudo apt-get purge guarddog
```

---

### Post by seawolf167 on 2011-03-03
Just noticed you said you were at a hotel... did you have to sign in through a "web portal" type page before you were able to access the internet? Can you open your network manager and select the hotel network to connect to (wifi or otherwise)?

---

### Post by lonewolf88 on 2011-03-03
> **seawolf167 said:**
> Just noticed you said you were at a hotel... did you have to sign in through a "web portal" type page before you were able to access the internet? Can you open your network manager and select the hotel network to connect to (wifi or otherwise)?
You are correct - I have to log on;  however Firefox goes straight to the home page, which of course is not found.

Unfortunately cannot email myself the text file, as KMail does not connect as well.

However closer examination shows a couple of lines (hope I type them correctly)

Reject tcp -- anywhere, same for udp.

Is this a problem?

(And thanks so much for the help!)

---

### Post by seawolf167 on 2011-03-03
Run this command to get a list of your rules with line numbers

```
iptables -L INPUT -n --line-numbers
```

then run this command to remove the rules for rejecting all traffic

```
iptables -D INPUT *<line_number_here>*
```

If you want to use a GUI to edit the iptables once you get back online, the only I suggest is GUFW

```
sudo apt-get install gufw
```

---

### Post by lonewolf88 on 2011-03-03
> **seawolf167 said:**
> Run this command to get a list of your rules with line numbers

```
iptables -L INPUT -n --line-numbers
```then run this command to remove the rules for rejecting all traffic

```
iptables -D INPUT *<line_number_here>*
```If you want to use a GUI to edit the iptables once you get back online, the only I suggest is GUFW

```
sudo apt-get install gufw
```

Thanks, will try above and report back!

---

### Post by lonewolf88 on 2011-03-03
The command (first one) did not work, but reading help in iptables I managed to get the lines listed, but unfortunately in groups of 4, each line in each group numbered 1 to 4.

Did I miss some thing here?

Also reading the help file, I saw "F" flush command.  Does this replace "D"?

Can I use a generic command to flush and reset all the iptables?

---

### Post by seawolf167 on 2011-03-03
> **lonewolf88 said:**
> Also reading the help file, I saw "F" flush command.  Does this replace "D"?

Its been a while since I have manually edited the iptables, you're right, the -F command should allow all traffic in and out, try that to revert them to defaults. The -D command allows you to individually delete rules.

---

### Post by lonewolf88 on 2011-03-03
> **seawolf167 said:**
> Its been a while since I have manually edited the iptables, you're right, the -F command should allow all traffic in and out, try that to revert them to defaults. The -D command allows you to individually delete rules.

That did flush the tables (when I did a list command showed them all clean), but not for long.

I ~think~ I know what the problem may be.

Guarddog still seems to be running, although the command to purge same (which you kindly listed previously, tells me it is not installed.

However at boot, I notice a message flash by about starting Guarddog firewall.

Anything else you can suggest to get rid of Guarddog?

---

### Post by seawolf167 on 2011-03-03
First get a list of services

```
ls /etc/init.d
```look for the guarddog service, then remove it with 

```
sudo update-rc.d *<servicename> *remove
```

---

### Post by lonewolf88 on 2011-03-03
> **seawolf167 said:**
> First get a list of services

```
ls /etc/init.d
```look for the guarddog service, then remove it with 

```
sudo update-rc.d *<servicename> *remove
```

Well, the list command showed guarddog running.

I had to use -f to force the removal, message "removing sytem startup etc.", but it is still there.

Maybe Guarddog is malware?

Is there a more powerful command that you suggested?

Just wondering, should I download the Guarddog tarball to a USB stick through windows, and reinstall, then reset.   I would rather avoid this if I can, as I am a novice, and might get into even more trouble!

---

### Post by seawolf167 on 2011-03-03
If the following doesn't work, I'm out of ideas, [here ]("http://www.simonzone.com/software/guarddog/manual2/index.html")is their online manual (though I didn't see anything specific about uninstalling the package)

stop any running service

```
sudo /etc/init.d/guarddog stop
```

ensure its completely removed

```
sudo apt-get purge guarddog
```

backup and delete the rc.firewall file

```
sudo cp /etc/rc.firewall ~/rc.firewall.backup
sudo rm /etc/rc.firewall
```

flush your iptables

```
sudo iptables -F
```

reboot

---

### Post by lonewolf88 on 2011-03-03
> **seawolf167 said:**
> If the following doesn't work, I'm out of ideas, [here ]("http://www.simonzone.com/software/guarddog/manual2/index.html")is their online manual (though I didn't see anything specific about uninstalling the package)

stop any running service

```
sudo /etc/init.d/guarddog stop
```ensure its completely removed

```
sudo apt-get purge guarddog
```backup and delete the rc.firewall file

```
sudo cp /etc/rc.firewall ~/rc.firewall.backup
sudo rm /etc/rc.firewall
```flush your iptables

```
sudo iptables -F
```reboot

Well, that seems to have fixed it. (apologies for delay, fell asleep!)

Thank you so much for your help; I owe you a beer or three!

Weird stuff though - the first command said it had stopped Guarddog;  the second command said Guarddog didn't exist!

(Fairly new to this stuff, as you can tell - is there a tutorial covering all the commands and others n- something like a basic DOS course I did many years ago) online somewhere, and which can be printed out?)

Also, when you post the code here, how do you format it in a box as you and others do?

Finally, thanks so much once again!

---

### Post by seawolf167 on 2011-03-03
Glad you got it working!

[LIST]
[*]You can start with the basics from the link in my sig "linuxcommands".
[*]For more on writing bash scripts, [see here]("http://mywiki.wooledge.org/BashGuide")
[*]For an older Ubuntu Guide Book, [see here ]("http://www.ubuntupocketguide.com/index_main.html")(most of the basics are the same, though some packages have changed like Grub -> Grub2)
[*]Google is a very good resource to search for more how-tos or questions
[*]Man pages are always a good resource, simply type
[/LIST]

```
man *commandname*
```

in a terminal

To format forum posts, there is a little # button when formatting your reply, simply put your code inside the code tags

---

### Post by lonewolf88 on 2011-03-03
> **seawolf167 said:**
> Glad you got it working!

[LIST]
[*]You can start with the basics from the link in my sig "linuxcommands".
[*]For more on writing bash scripts, [see here]("http://mywiki.wooledge.org/BashGuide")
[*]For an older Ubuntu Guide Book, [see here ]("http://www.ubuntupocketguide.com/index_main.html")(most of the basics are the same, though some packages have changed like Grub -> Grub2)
[*]Google is a very good resource to search for more how-tos or questions
[*]Man pages are always a good resource, simply type
[/LIST]

```
man *commandname*
```in a terminal

To format forum posts, there is a little # button when formatting your reply, simply put your code inside the code tags

Great, thanks.

In your opinion, should incoming pings be allowed.  Steve Gibson grc.com in his software "Shields Up" reckons it is a bad idea.

---

### Post by seawolf167 on 2011-03-03
Usually you want to silently drop them so *they* can't get any info back, but I wouldn't really worry about it.

If you get paranoid or are security conscious, use GUFW as your firewall

```
sudo apt-get install gufw
```

I promise you won't have the same problems you had with guarddog! Then enable the firewall and "poke" holes in it for whatever services you need (i.e. torrent port, ssh port, WoW port, etc.)

---

### Post by lonewolf88 on 2011-03-03
> **seawolf167 said:**
> Usually you want to silently drop them so *they* can't get any info back, but I wouldn't really worry about it.

If you get paranoid or are security conscious, use GUFW as your firewall

```
sudo apt-get install gufw
```I promise you won't have the same problems you had with guarddog! Then enable the firewall and "poke" holes in it for whatever services you need (i.e. torrent port, ssh port, WoW port, etc.)

Thanks, using GFUW now.

Once again, appreciate your help. :popcorn:

---

