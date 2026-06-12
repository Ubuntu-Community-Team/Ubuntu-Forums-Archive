---
title: "Network Manager icon location"
date: 2011-09-02
forum: General Help
---

### Post by geomcd1949 on 2011-09-02
Was trying to configure my system so that it stops incessantly asking for my password. Found an article that said go to the Network Manager icon. That stumped me! Could someone please tell me where I would find the Network Manager icon? Thanks! [Obviously, I'm a new Ubuntu user.]

~George

---

### Post by Old_Grey_Wolf on 2011-09-02
What version of Ubuntu are you using? It may affect whether there is an icon or not.

---

### Post by geomcd1949 on 2011-09-02
Thank you, Old Grey Wolf,

I am using the 11.04 Natty Narwhal.

~George

---

### Post by Old_Grey_Wolf on 2011-09-02
Natty does not have the icon. To get to the Network Manager, click on the Ubuntu logo on the top left of the screen, then search for "network connections". I don't think it is going to help though. It seems like your problem is with the "Ubuntu keyring password". Google on that phrase.

If you are having other problems with nagging password, read this Ubuntu documentation [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Use at your own risk!

---

### Post by geomcd1949 on 2011-09-02
Thanks Wolf,

I've seen in other threads that folks are having difficulty with the keyring password. I expect I'll come across that problem later on as I get further into Ubuntu. But I'm just attacking one problem at a time, and the current one is the need to enter the password every time I leave the computer for a few minutes. Any suggestion as to how to deal with this is greatly appreciated.

I did notice that, in installing Ubuntu, what was supposed to happen was that no password would be needed if a box was checked (or maybe unchecked - I forget the exact sequence) when filling in boxes during the setup process. But apparently that didn't take effect, and the password is still [frequently] required.

~George

---

### Post by grahammechanical on 2011-09-02
Are you trying to make a wireless connection to your router/modem? The network manager icon should be in the top panel towards the right. If you are connected by ethernet it will look like two arrows going in opposite directions. If you are connected by wireless it will look like four arcs radiating upwards.

If the icon looks like an open fan (that you wave with your hand), then you are not connected. You will also see messages telling you the same things. All this information helps us to help you. At the moment we are guessing.

When you click on the network icon you should see a list of in ranger wireless networks. Your network should be in the list. Click on it. You will be asked to authenticate the connection. Get the password or pass phrase wrong and it will not connect and you will be asked to enter the pass phrase again. If network manager is set to a different encryption method to the method used by the router, then the connection attempt will fail because the two machines are not talking the same language. You will be asked to authenticate again.

You should understand that Linux in general and Ubuntu in particular insist on requiring authentication to make certain adjustments to the system. If you do not like this and want to disable this feature, then finding the network manager icon will not help you.

Regards.

---

### Post by Old_Grey_Wolf on 2011-09-02
> **geomcd1949 said:**
> ...the current one is the need to enter the password every time I leave the computer for a few minutes.

Is it the need to enter the sudo password after the 15 minute timeout, or are you referring to the screen-saver password? If it is the screen-saver password, you can turn that off in the System > Preferences > Screensaver options. If it is the 15 minute timeout, then you can lessen the pain by using the "sudo -i" command from the "https://help.ubuntu.com/community/RootSudo" link I provided.

> I did notice that, in installing Ubuntu, what was supposed to happen was that no password would be needed if a box was checked (or maybe unchecked - I forget the exact sequence) when filling in boxes during the setup process. But apparently that didn't take effect, and the password is still [frequently] required.

Checking the box doesn't eliminate the need to enter the keyring password. This problem is usually caused by the Ubuntu keyring password still being required even after enabling auto login. Once again search on "Ubuntu keyring password". 

I don't think I want to go into bypassing Ubuntu's default password requirements. :)

---

### Post by geomcd1949 on 2011-09-02
Dear GrahamMechanical,

You must be psychic - I intended to post a question about establishing a wireless connection with an adapter in the next few days. How you determined I needed this answer is amazing. Thank you. What you wrote allowed me to set up a wireless connection.

The problem I dealing with, and writing here about, is that after three or four minutes of inactivity, my screen goes dark, and when I return to the computer, it asks for my password. I would like to stop this process, or at least lengthen the interval between times I'm asked for a password.

Old Gray Wolf speaks of "the need to enter the sudo password." I don't yet know what a sudo password is. What happens is, if I don't type anything or move the mouse for about three or four minutes. The screen goes dark. Then, when I move the mouse, or hit "Enter," a screen pops up demanding my password. I type in the password, then the screen appears as it did before it went dark.

If this is what you mean by the "screen-saver password," then that is what I want to disable. Can you please tell me where [exactly where] to find the Systems link [or icon] to follow, to  drill as you suggest, to System>Preferences>Screensaver options.

Thanks!

~George

---

### Post by Old_Grey_Wolf on 2011-09-03
To get to the Screensaver in Natty, click on the Ubuuntu icon in the top left of the screen, search for "screensaver", then click on the screensaver icon. Uncheck the box with Lock screen when screensaver is active.

---

