---
title: "Centrally managed antivirus options?"
date: 2009-11-02
forum: General Help
---

### Post by abishur on 2009-11-02
Hey guys, I was wondering if anyone knew of a good centrally managed anti-virus software that I can run on my ubuntu server for windows machines.

Here's some further information that might be useful in answering the question.

1)  I don't need it to scan my linux computer.  I'm well aware of the fact that Ubuntu requires no anti-virus. ;)

2) This is mostly a proof-in-concept project so I'd prefer not to have to buy additional software if things don't work out.

3) My setup is a couple year old dell (XPS M140) laptop that I don't use anymore and so I decided to turn it into a all-in-one server (e-mail, dhcp, web-proxy, web-filter, etc) so far it runs everything AMAZINGLY, but an anti-virus software that uses that ONE computer to scan EVERY other computer (5 for the moment, but it will increase if this works well) seems like a sure fire way to drag down my little machine.  So instead I'm looking for something that installs clients to the PCs, but uses the main comptuer to centerally instruct and pass out virus definitions to the other machines.

4) As much as possible, I'd like for the software to be largly automated after setup.  If I have to manually intiate the virus scan, it's not much use and I might as well just install AV software on each computer locally. (And to answer anyone who's thinking, "Hey, why don't you just install AV software on the computer locally?" the answer is that this is a proof-in-concept work, simply put I'm simply trying to figure out if it CAN be done at all)

I'm currently researching bitdefender because I've seen it mentioned in some other threads, but if anyone knows of another piece of software that does what I'm looking for, I'd love to get your input on it!  Please let me know if you need any other info!

---

### Post by Rebelli0us on 2009-11-02
In windows I use the Scheduler to wake PCs at night to run antivirus. I haven't tried this in Linux but gnome-shedule can probably do the same..

---

### Post by abishur on 2009-11-18
I suppose that *could* work.  To be honest I was hoping for something with a little more centralization in the management department.  I.E. I could push new virus updates, initiate a manual virus scan if I wanted to (in addition to a regualarly scheduled auto-scan), stuff like that.

Webroot is a good example of what I'm looking for.  Bitdefender seemed to have something that *could* work, but it would cost money to get it (and hey, that kinda defeats the whole purpose of an open source server, right :p)

---

### Post by abishur on 2009-11-23
Clam AV *almost* does what I want it to.  At the very least I can install the windows client on my machines and then tell them to get the updates from the server rather than the internet.  It would be really awesome if it had an interface that would check the virus status of the "client" workstations virus definitions/last scan.  And allow you to update them and schedule weekly virus scans.

Does anyone else know of a product that does this?  I may have been unclear in my initial post so let me really lay out what I'm looking for

1. On the server I really only need it to manage the clients.  I.E. it tells the clients to run weekly (or whatever schedule) anti-virus scans/updates, but it doesn't do the scanning/updating itself.

2. It would be nice if it could deploy the client software over the internet, but I'm not afraid to use the tried and true sneakernet to install/configure clients

3. On the clients' end, the software runs the scan using the client's own resources and updates off the server.

Clam AV comes so close it's kinda sad.  If I knew a little more about programming, I could probably write some low level GUI that could check the time-stamp of the virus definition on the client computer and display it on the server computer... but I don't know more about programming so I guess it's a moot point.

---

