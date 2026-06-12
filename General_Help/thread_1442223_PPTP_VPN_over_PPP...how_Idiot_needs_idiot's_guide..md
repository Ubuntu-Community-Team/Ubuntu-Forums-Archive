---
title: "PPTP VPN over PPP...how? Idiot needs idiot's guide..."
date: 2010-03-29
forum: General Help
---

### Post by t0p on 2010-03-29
Recently I was given a PPTP VPN account with a commercial VPN provider.  I can connect to the VPN server just fine when using *network-manager*.  But I like to use my cellphone as a bluetooth modem, and the phone just won't play nice with *network-manager*.  I have to do dial-up networking instead, which I do with *Gnome-PPP*.

*Gnome-PPP* has no provision for using VPN connection.  And for some reason I have never been able to get my head around configuring *ppp* manually: all that *pon*, *poff*, chatscripts and whatever makes me dizzy just to think of it!  I'm sure it's all very simple really, but I seem to have a mental block when it comes to *pp-blinking-p*.

I know there's a way to use my PPTP VPN account via *ppp*, but the *pptp* and *pptpsetup* manpages make my head swim! And Google's no help either - usually she's my best friend, but on this subject she's a cold, uncaring witch.  What I need is for some kind soul to spell it all out for me - preferably by typ...ing...slow...ly, ALL IN CAPS and no long words.  An idiot's guide, for an idiot.

I'm using Ubuntu 9.04.  Can anyone help me?  Please?

Hellllpp!!  :(

---

### Post by t0p on 2010-03-30
Bump dammit!  BUMP!!

---

### Post by t0p on 2010-04-01
Is there something really odd about what I'm asking?  Am I the only person on the entire site who wants to use PPTP over a dialup connection?

I know there has to be *someone* in these forums who knows how to do what I'm asking.  So please please please please please please please please *HELP ME*!!!!!

The closest I've found is [this]("http://ubuntuforums.org/showthread.php?t=28396&highlight=pptp") - but it's for Hoary/Breezy/Edgy ffs, and I'm sure the commands involved are now deprecated or some such sugar.  And I've never been comfortable trying to run ppp0 over the command line anyway...

C'mon peeps!  Help out a meerkat willya?

---

### Post by t0p on 2010-04-03
Okay.  Does anyone know how to use a phone as bluetooth modem through network-manager?  This basically entails getting a dialup connection to work with network-manager.  If I can do *that*, I should then be able to use it with the PPTP VPN.  Cheers.

---

### Post by prodigy_ on 2010-04-03
Doesn't your VPN provider support Linux at all? Not even Ubuntu?

---

### Post by t0p on 2010-04-03
> **prodigy_ said:**
> Doesn't your VPN provider support Linux at all? Not even Ubuntu?

The problem isn't at the provider's end.  If I'm browsing with wired connection (eth0, or usb0 if I'm using my cellphone connected with datacable) and network-manager, everything works fine.  I've configured network-manager to use the VPN connection, which has built-in PPTP compatibility.

The problem arises when I'm connecting in some other way that doesn't involve network-manager.  When I use my cellphone as bluetooth modem I have to go through ppp.  At the moment I use Gnome-PPP as a front-end, as I find the inner workings of ppp too complicated for my tiny mind.

Anyway, the issue isn't about the provider or Ubuntu.  It's all about *me*, because I don't know how to do it.

---

### Post by ralphycarlton on 2011-03-17
Well, after a couple of days of pulling my hair out, all is sort of well. I found the following:
  1) Dial up networking was removed from Network Manager on purpose. Why? I have
      no idea.
  2) As you found out, you can configure gnome-ppp to connect via dial-up. Network 
      Manager, however, will not recognize or use the connection.
  3) Network Manager uses vpnc on the backend for VPN connection. You can use it with
      gnome-ppp, but you have to initiate it from the command line.
  4) From a terminal console, simply enter #sudo vpnc ... you should be prompted for
      your VPN specifics.
  5) vpnc will use one of two configuration files; 1) /etc/vpnc/default.conf and if that is not
      found, 2) /etc/vpnc.conf. Neither were present on my system (Lucid 10.04).
  6) After doing a sudo chmod 777 /etc/vpnc, I went in and created the default.conf so I 
      didn't have to answer the prompts everytime. I changed the read/write/exec
      permissions back to root only after creating the file.
  7) Now you can create an application launcher to fire it off or just open a console and
      enter vpnc and go. It works.

---

### Post by saeed144 on 2011-08-01
I have set up PPTP VPN server on ubuntu.
But accounts are open for concurrent simultaneous connections. means there can be many users using one account at the time.
i need to limit that to one user at the time.
anybody knows how it can be done?

---

