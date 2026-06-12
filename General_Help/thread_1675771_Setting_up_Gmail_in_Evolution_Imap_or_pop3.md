---
title: "Setting up Gmail in Evolution: Imap or pop3"
date: 2011-01-26
forum: General Help
---

### Post by kedarm on 2011-01-26
Hi,

I'm trying to set up my gmail account with Evolution. I am trying to set up a mail client where -
1) All the mails are stored locally, so that I can work offline. When I reconnect, the client (Evolution) syncs with the server - sends emails and updates any changes.
2) All the labels/folder system to be respected and retained.

After struggling with various sites that argued Pop3 and IMAP (numerous blogs and google searches), I came across this conclusion (pls correct them if they are wrong)-

1) Pop3 allows mails to be stored locally, but will not break them up into folders.
2) IMAP will allow the folder system, but will only store the headers of mail on the local server, and the content will be downloaded as per request.

I had a couple of questions -
1) Will Pop3 access allow syncing between the local version and the server version? For instance, a mail read in Evolution should be marked as read when I sign into the web-interface as well.
(I can always create a filter/rule that replicates gmail filters)
2) Will IMAP allow me to store all mail locally (isn't this exactly what IMAP is not!)? The combination of imap-gmail-evolution was not so successful when I tried it out - too slow!

Thanks,
Kedar

PS: I would prefer Evolution over Thunderbird so that I can integrate the Calendar. However, if ThunderBird is the easiest solution, then it's fine too...

---

### Post by ajgreeny on 2011-01-26
I think you can set up gmail to do more or less what you are asking for in Q1, but it should be easy enough to find out.  However, pop3 does not sync in the same way that IMAP does, but just downloads mail, and then marks it as read, but leaves it in the gmail inbox, or if you want it will archive it, but it will still show in the All Mail box if you are using thunderbird or evolution as IMAP clients.

IMAP can be set to download and store complete emails rather than just headers if you want, and this can be very useful if you often find yourself in an off-line situation.  I think both clients, evolution and thunderbird can do things that way, but you will need to check that first.

---

### Post by kedarm on 2011-01-26
Hi,

Thanks for the reply.

I am trying to get IMAP to store local copies for me. I followed the instructions given [here]("http://www.murrayc.com/blog/permalink/2006/10/01/evolution-and-imap/") -
I did the following:
1) The account setup (Edit/Preferences/Mail Accounts/Edit/Receiving Options) has an “Automatically synchronize remote mail locally” checkbox which I checked
2) Right-clicking on a folder in the Sidebar and choosing Properties --> checking “Copy folder content locally for offline operation”.
3) Choosing File --> Work Offline Mode

When I did this, it spent a large amount of time receiving (or so I thought) email from the server. I think it got all the headers, but not the content. Right now, if I choose to see any email, it spends terribly large amounts of time retrieving mail from the server.

(The slow speed has been well documented all over the place, and that is one of the primary reasons for wanting the local copies of all mail).

Thanks

---

### Post by dandnsmith on 2011-01-26
If you use pop3 with gmail, you can set gmail to retain the inbox content on gmail or to delete each email downloaded - your choice.

It isn't the same behaviour as traditional pop3 servers.

---

### Post by VCoolio on 2011-01-26
If it's possible it's with IMAP, not POP3. Pop3 is one-way server-client traffic, no client-server. So use IMAP and then I think you'll need to find an option in your client to store all mail locally instead of per-request downloading from server. I'm not really sure, either I ticked the option in claws-mail or it does this automatically. It only stores new mail once I click it; but everyhing once opened is stored.

Edit: seems gmail pop3 is different. anyway, good luck

---

### Post by jkobbe on 2011-02-02
You may have figured this out by now, but here goes for others ...

To download entire messages rather than just headers, go to the Edit/Preferences menu item. with Mail Accounts selected in the left nav, your imap account selected in the center pane, click the Edit button. Select the Receiving Options tab. Check the box labeled "Automatically Synchronize Remote Mail Locally."

The help file for this option says "If you check this option, Evolution fetches the headers as well as the body of the message simultaneously. In this case, the time taken to open a message is comparatively less. In addition, you can download the mail for reading them offline, when you have checked this option."

---

