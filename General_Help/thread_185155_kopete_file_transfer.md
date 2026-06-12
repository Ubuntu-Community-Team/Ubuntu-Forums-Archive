---
title: "kopete file transfer"
date: 2006-05-31
forum: General Help
---

### Post by PsychoTrauma on 2006-05-31
I am using kopete to connect to the msn network and it seems I am having trouble transferring files. I can send them just fine but I can't receive them. In the chat session I see incoming file transfer but no window ever pops up allowing me to accept the connection. Is there something I need to do to accept the transfer other than wait for something to pop up? I have been a long time gaim user so I automatically assumed it would be a similar procedure.

---

### Post by CitizenKane on 2006-05-31
Do you have a router set up?  That could block incoming file transfers.  I have had similar problems on gaim.  If you do have a router you may want to just try plugging your computer straight into whatever kind of broadband modem you have.  A firewall (e.g. iptables) may also block the incoming transfers.

---

### Post by Randomskk on 2006-05-31
Double check there's no popup, as well - for me the window appears minimised, on the first screen, even when the chat window is on the second screen.

---

### Post by mycomputersucks on 2006-05-31
Like CitizenKane said this could be due to your router. Try opening ports 1863 and 80.

---

### Post by PsychoTrauma on 2006-05-31
Opening the ports worked thank you. Do I need both 80 and 1863 open though? I know the 1863 port is for the msn network but i'm not sure why it would need port 80 which is used for http.

It seems kopete can't receive files from msn 7.5 but if the person is using the new windows messenger live beta it works.

---

### Post by Dryer Lint on 2006-06-01
I'm also having similar problems with MSN file transfer.

All the neccessary ports are open, but I can only send files.
Receiving works for some people, it most likely depends on the Messenger program used.

Maybe we could collect information here about which clients can send to Kopete via MSN? And then sum it up in a bug report.

I can't seem to receive files from Trillian MSN users.

EDIT: Post the Kopete version you are using, too! I'm using 0.11.93 (0.12 Beta 2).

---

### Post by PsychoTrauma on 2006-06-02
I am using kopete 0.11.3

Windows messenger live 8.0 transfers work.

Windows msn messenger 7.5 transfers don't work. (no transfer window period)

Gaim 1.5.0 on windows  transfers don't work. (transfer window pops up but the file sits at 0 kbs)

Those are the only three people on my messenger use so that's all I can test atm.

PS. Could a mod please move this over to the dapper section.

---

