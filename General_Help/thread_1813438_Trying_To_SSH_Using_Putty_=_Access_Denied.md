---
title: "Trying To SSH Using Putty = Access Denied"
date: 2011-07-27
forum: General Help
---

### Post by swappedsr on 2011-07-27
I am using Putty on a Windows Xp machine to try and SSH into an UBUNTU 10.04 server box and I am getting access denied for both the root and Administrator account at login.  I have been at this for over a half a day trying to figure this out.  I tried commenting out PasswordAuthentication, changing it from the default yes to no, nothing works.  At a loss, and really could use the help.

---

### Post by spiky001 on 2011-07-27
Hi I take it you have the ssh server installed, sorry to state the obvious

---

### Post by Bachstelze on 2011-07-27
> **swappedsr said:**
> I am getting access denied for both the root and Administrator

You cannot login with the root account in Ubuntu, and there is no "Administrator" account. You should use the account you created when you installed the system.

---

### Post by FizzerJE on 2011-07-27
Hi,

Would not be a good thing if you could ssh and login using root...

Standard setting I apply immediately to at every new install

/etc/ssh/sshd_config 


Port 29992     <<< change to what ya want can leave at default 22
LoginGraceTime 30 <<< Extend if you are slow :)
PermitRootLogin no <<< A definate

AllowUsers YOUR_USER_NAME-HERE
UseDNS no <<< Only if local, no dns, can't help with slow response.

There is much more, just the basics...

Also check the ssh is running as a service...

```
sudo service ssh start
```

But is you get a deny is is more than likely because you are trying root..  use you username as stated above..

ssh, I belive, is not installed by default. But I am a noobie to Ubuntu..  No joy with service start...  Then

```
sudo apt-get install ssh
```

---

### Post by swappedsr on 2011-07-27
The SSH server is installed.  

I created the Administrator account when the I built the server.  Neither this account or root works.  I can SSH locally on the problem server, which seems to work fine.

---

### Post by FizzerJE on 2011-07-27
```
ifconfig
```

is network setup.

ssh local will use lo interface...  that is always configured

Also any changes to sshd_config will need a service restart

---

### Post by swappedsr on 2011-07-27
Yes, network is setup, however I have problems with setting a static ip address for some reason, now when I go into network connections I don't have any interfaces listed.  I tried adding an interface 'eth0' however that did nothing and never seemed to take the gateway when I added it, very strange, it kept leaving it 0.0.0.0.  Anyway, somehow it is getting an address via dhcp. I don't know how to fix this yet.  But, it seems like it is functioning as I am connected on the local network and the internet and I can reach the server through SSH, just keep getting access denied.

---

### Post by FizzerJE on 2011-07-27
Sorry, not reading your post correct.

Do you get a login prompt..  and the access denied when trying the account.

I had the issue when my local KB was set to US and i am using GB on the putty client, and one of the password phrases included an @ which came as a " in US KB.

---

### Post by bodhi.zazen on 2011-07-27
Did you forward the port ? Are you using keys ?

Output of ssh -vvv from another linux box or review the logs on the server.

---

### Post by FizzerJE on 2011-07-27
What does your /var/log/auth.log

```
tail -n 20 /var/log/auth.log
```

for last few entries

---

### Post by swappedsr on 2011-07-27
Yeah I can get to a login prompt from putty, but both accounts get access denied and I know the passwords are right.  I don't need to forward ports as I am on the same subnet, so there is no firewall into play yet, but I will be setting that up once I get this squared away.

---

### Post by FizzerJE on 2011-07-27
try a login..  then post the log...

UFW..  sorry I came from CentOS, that goes in the bin along with [I]sudo apt-get purge network-manager network-manager-gnome -y
[/I] as standard for me... I like it the manual hard hard  :)

---

### Post by swappedsr on 2011-07-27
Jul 27 16:42:34 PFWDEV sshd[1384]: pam_winbind(sshd:auth): getting password (0x00000388) 
Jul 27 16:42:34 PFWDEV sshd[1384]: pam_winbind(sshd:auth): pam_get_item returned a password 
Jul 27 16:42:35 PFWDEV sshd[1384]: Failed password for invalid user Administrator from 10.185.10.34 port 2716 ssh2

---

### Post by FizzerJE on 2011-07-27
Theres ya reason..

for invalid user Administrator

I always wonder when users have capitalisation..

look at you users

quick and dirty is

```
cat /etc/passwd 
```

 see if it is there..  Should be near the bottom..  first 500 are system only

Users are case sensitive on unix... ;)

---

### Post by swappedsr on 2011-07-27
Genius!  Thank you!!!  

Is there a reason I can't login as root though, I think in the config file it does say it is enabled to do so.  I know it isn't good to do, but just curious.

---

### Post by swappedsr on 2011-07-27
Also, anyway to remedy the static ip address?  How do I enter that in for eth0 if I am doing it the gui way in the network connections app.  I don't have any connections listed there.

---

### Post by swappedsr on 2011-07-27
Here is the screenshot of what I am talking about.  Eth0 has a dhcp address and there aren't any interfaces shown in the network connections list.  I think I may have deleted it by accident and I tried putting in eth0 and adding a static address, subnet, gateway to no availability.

---

### Post by FizzerJE on 2011-07-27
NP..

Sorry I use ubuntu because i have soooo  many issues geting XBMC working in Linux.

I get rid of most automated config...

You can try...

```
sudo ifconfig ethx 192.168.1.x netmask 255.255.255.0
```

for local no gateway...

Change as appropiate..  'x' bits or local sub-net...

BUT

I do not know what the network manager does..  may overwrite..

GL

---

### Post by FizzerJE on 2011-07-27
By the way...

root over ssh is best not enabled.  It is a good thing you can't.

After all it only takes logging in with your user..  Then ```
sudo su -
``` for a more permanent solution ;)

I add AllowUsers as it is 1 small security step (they all add up)..

Any tomfool can guess root, but use an AllowUser in sshd_config, then they have to guess the user before they even start... along with a syn rule in iptables to stop too many incorrect logins, the job is so much harder.. (don't ask me how to do that in UFW).

An TBH 'A'administrator is not much better.

I am paranoid though...  :)

---

### Post by swappedsr on 2011-07-28
Thanks Fizzer, the static address worked with that command.  It still didn't add the entry in the network connections app, but now shows the ip address when I do a ifconfig.

---

