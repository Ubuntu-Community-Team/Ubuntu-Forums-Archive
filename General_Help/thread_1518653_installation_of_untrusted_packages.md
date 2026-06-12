---
title: "installation of untrusted packages"
date: 2010-06-26
forum: General Help
---

### Post by gokulsurendiran on 2010-06-26
Hi all!,
I have a lenova B450, installed ubuntu 10.04 netbook remix(dual boot with win xp), everything works fine, even installed some games through ubuntu software center.

I tried to install cd burning software, i received the following message.

Requires installation of untrusted packages 

The action would require the installation of packages from not authenticated sources.

Even after i gave OK there was no response. Now when i tried to install games also same message & no response.

Kindly some one help to solve this problem.

---

### Post by siabost on 2010-06-30
Hi,

I have a similar problem with the Ubuntu Software Centre but you can get round it by going to System/Administration/Synaptic Package Manager.
Search for your program, mark it for installation (tick box), click "Apply" button, OK/Mark the window that results listing the items to be installed and click "Apply" once more.
Whilst it will still say it's from an unauthenticated source Synaptic will actually install it.

I'm still looking for a way to fix the "Unauthenticated Source" issue re The Software Centre as it seems daft to list products in there that you have no (obvious) way of loading.

Best :p

---

### Post by bruno9779 on 2010-06-30
It is quicker done in terminal.

If you open the details in the error prompt, it will list there all the affected packages.

You can copy them all and the paste (shift+ins) in a terminal after "sudo apt-get install "

installing them one by one in synaptic is time consuming

---

### Post by siabost on 2010-06-30
Hi,

bruno9779 is quite right of course but if you want to use The Ubuntu Software Centre and avoid getting the install blocked by the message "Unauthenticated Source" then I've just found out that this works: -

Go to System/Administration/Software Sources. Go to third tab "Updates" & tick the "Proposed Updates" & "Unsupported Updates" options. Then "Reload" when it asks you to.

This works for me and I'm happy with it but I'm not sure if making the above changes leaves you more open to "dodgy" updates - but I've certainly never had a problem with these settings in the past.

Best

---

