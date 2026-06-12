---
title: "Best way to sync Evolution across 2 x Ubuntu machines"
date: 2009-08-06
forum: General Help
---

### Post by VipX1 on 2009-08-06
I know have 2 x Ubuntu machines now, my laptop and my desktop. I've a very similar set-up on both but the desktop has alot more processing power. I only use the laptop when I'm out. However when I do use the laptop it pulls down mail from the mail server and then those mails are not on the desktop. I'm using gmail and evolution, on both machines.
Can I get the 2 x machines to sync when they are on the same local network together, without me having to connect via ssh from one machine to the other.

---

### Post by howefield on 2009-08-06
Are you pulling your mail down to your machines via POP3 ? If so, I think IMAP will better suit your needs.

[http://mail.google.com/support/bin/answer.py?hl=en&answer=75725](http://mail.google.com/support/bin/answer.py?hl=en&answer=75725)

---

### Post by VipX1 on 2009-08-06
I am using pop3. What is the difference with IMAP, what will it do?

---

### Post by howefield on 2009-08-06
Well, if you care to read the link I gave you, you will see that it...

"IMAP also provides a better method to access your mail from multiple devices. If you check your email at work, on your mobile phone, and again at home, IMAP ensures that new mail is accessible from any device at any given time".

Which seems to describe what you want to do.

---

### Post by VipX1 on 2009-08-06
Sorry I thought that was a signature... Thanks, that looks good.

---

### Post by giggins on 2009-08-06
+1 for howefield's suggestion.

> **VipX1 said:**
> I am using pop3. What is the difference with IMAP, what will it do?

Check this [Wikipedia article]("http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol#Advantages_over_POP") out.

---

### Post by zarthon on 2009-08-06
I have used a file sync program called unison to synchronize files.
It has a good graphic interface but still requires being on the same LAN if you don't have a VPN or can't sync to and from a server you or a friend controls.

The unison program will synchronize by updating new files in both directions so it will make the two trees identical which may not be what you want for this purpose. 

You can use synaptic or apt-get to install unison and unison-gtk

Other solutions:
You can configure your evolution on your laptop to not delete email from the pop server when it is downloaded.
go to edit -> preferences
select thee account
click edit
select the receiving options tab
check the check box 'leave messages on server'

Use a script to synchronize.  I assume you have been using commands to sync since you mention ssh. You could script what you have been doing in bash or python...  I would probably use rsync and make a link in your menu or launcher to your script. This would be a good solution if you want to do a one way sink only updating items from the laptop to the desktop but not the other way around. 

If you have another account that uses IMAP you can drag messages from any account into the IMAP folders in evolution and then go to the other comptuer and synchronize this folder with the IMAP server.

Note that the receiving options are different and more complex for IMAP. It may take some time to configure but most ISP's offer IMAP as an option and it's alot more flexible than POP.
I can't remember if gmail supports imap.

---

### Post by zarthon on 2009-08-06
I agree that IMAP may be a great solution. I was multitasking and did not see that others were posting while i was writing.

Unison is still worth a look.

Most ISP's like comcast or verision offer IMAP so you could use these servers to move mail between machines.
It does not matter that the email was not originally to the account that uses imap. The protocol preservers headers.
Note though that you will have the mail in a local folder using this method. I have not tried dragging mail or folders from a local or imap account to an account configured to use pop.
You would end up with a folder " mail from laptop" in another account or under local folders.

---

### Post by VipX1 on 2009-08-06
I've checked 'leave messages on server' on my laptop, as quick solution.
IMAP looks much better than POP3 and gmail does support IMAP. I'll make sure I know what I doing first and then I'll change over.

Thanks, much appreciated.

---

### Post by VipX1 on 2009-08-07
I've set IMAP on my existing gmail account with evolution as the client. I have reconfigured Evolution on both the laptop and the desktop for IMAP. The problem I have now is Evolution is syncing with the folders in gmail. There is only one folder in gmail the inbox and then the default folders.. My Evolution folders are ignored and none of the mail comes into my Evolution inbox so my mail Rules are ignored also. I don't think I can import my folders into gmail so they sync correctly with folders in Evolution. I have just under 2,000 mail in about 60 different folders. Just the thoughts of rearranging them makes me tired.. I deleted the original messages from gmail so I don't think it can be done.  So I think I'm back to square one..

---

### Post by VipX1 on 2009-08-07
I almost have all my POP3 folders dropped into my new IMAP folder and the changes are synced across both machines. However, some folders will not move and they return a non-de-script error when I try move or copy them. Then when I try to Empty Trash in Evolution I get "error while expunging folders". I can't delete the problem folders either.
I see in other posts this is a recurring problem for Evolution but I can't find a working solution. Has anybody a working solution to the Empty Trash error?

---

### Post by dcstar on 2009-08-07
> **zarthon said:**
> I have used a file sync program called unison to synchronize files.
It has a good graphic interface but still requires being on the same LAN if you don't have a VPN or can't sync to and from a server you or a friend controls.

The unison program will synchronize by updating new files in both directions so it will make the two trees identical which may not be what you want for this purpose. 
...........

Pointless for this requirement as it may well overwrite files that contain data that is not in the newer file.

---

### Post by dcstar on 2009-08-07
> **VipX1 said:**
> I almost have all my POP3 folders dropped into my new IMAP folder and the changes are synced across both machines. However, some folders will not move and they return a non-de-script error when I try move or copy them. Then when I try to Empty Trash in Evolution I get "error while expunging folders". I can't delete the problem folders either.
I see in other posts this is a recurring problem for Evolution but I can't find a working solution. Has anybody a working solution to the Empty Trash error?

Are you sure you have sufficient quota in the IMAP account?

---

### Post by VipX1 on 2009-08-08
I am only using 3% of my gmail storage allowance.
I have uninstalled Evolution with synaptic, deleted my .evolution file and reinstalled Evolution. Then Evolution started empty with just the account settings and it pulled down all the IMAP folders that I moved successfully earlier on. The result was I ended up with the working folders only in Evolution and 'Empty Trash' did work. 

I tried to recreate one of the problem folders so I could start afresh and Evolution would not create it. Just the new folder name would of been the same. It will not even create half of the folder name in a 2 word folder name.
[I]e.g.
N.B."Old folder being Inbox/Software Suppliers"

[/I][COLOR=Blue][COLOR=Navy](Right Click on Inbox)[/COLOR] [/COLOR][I][COLOR=Blue]Create Folder, Software Suppliers
[COLOR=Red]ERROR, can't create folder INBOX/Software Suppliers[/COLOR][/COLOR]
[COLOR=Navy]
[/COLOR][/I][COLOR=Blue][COLOR=Navy](Right Click on Inbox)[/COLOR] *Create Folder, Software*
[COLOR=Red]*ERROR, can't create folder INBOX/Software*[/COLOR][/COLOR]
[COLOR=Navy](Right Click on Inbox) [COLOR=Blue][I]Create Folder, Software1
[COLOR=Green]_No_ Error!

[/COLOR][/I][/COLOR][/COLOR]The Error does output the "Inbox" different to the way that it exists, the error outputs "INBOX" and the folder is "Inbox". However, that does not effect the other folders.

[COLOR=Black]*I started up the laptop this morning and I've no Top [/COLOR]Panel and no Bottom Panel anymore?? I don't know what I did to effect the display?? I have desktop icons only! Oh, and my Screenlets.
Great Fun, I love Computers.

---

