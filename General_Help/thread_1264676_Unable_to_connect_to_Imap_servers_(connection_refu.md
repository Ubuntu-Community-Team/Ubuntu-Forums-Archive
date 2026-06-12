---
title: "Unable to connect to Imap servers (connection refused) on any mail client with 9.04"
date: 2009-09-12
forum: General Help
---

### Post by house055 on 2009-09-12
Hello, 
Since I have done a clean install of Jaunty on my desktop I have been unable to connect to my gmail account. I have tried Evolution, Mozilla and Opera. All give me roughly the same error. 

Evolution says:
"Error while scanning folders in"imap.gmail.com.""
"Could not connect to imap.gmail.com: connection refused"

Thunderbird says: 
"Could not connect to mail server imap.gmail.com; the connection was refused."

Opera mail client says:
"The connection with the IMAP server was unexpectedly interrupted."

I have checked and rechecked my settings and ports on all clients at least a dozen times each. I have tried changing from SSL to TSL, and vice versa and everything in between. I have fresh installed all clients over and over. I have come to the conclusion that it is not an ISP problem, since my ipod touch, windows xp notebook, and vista notebook all connect to imap.gmail.com with no problems. 

One thing that doesn't help me is that this is my first experience working with a unix platform. Consider me an UberNewb. If there is any more info that is needed to better diagnose the problem. Please respond. 
Thank you,
Paul H

---

### Post by Rocket2DMn on 2009-09-12
Gmail IMAP settings should be as follows under Account Settings -> Server Settings:
servername: imap.gmail.com
port: 993
username: *your email user name, without @gmail.com*
Security settings: SSL (don't check "Use secure authentication")

Under the high level setting for the email account, the full email address is given under "Email Address".  Be sure the Server Type listed at the top is IMAP Mail Server.

---

### Post by house055 on 2009-09-12
Thank you for your quick response. The only thing different in your listed settings and the ones I was currently using was dropping the "@gmail.com" from my user name (even though google says to include the @gmail.com in the user name field). Despite what google says I tried anyways and this does not work in any of the mail clients I have listed. I still receive the same error messages in all clients.

Is there any setting or script in Ubuntu that could be interfering with this connection? 

Is there anything I can do to gain further information about this error?

---

### Post by whitethorn on 2009-09-12
Have you set enable imap in gmail itself?  You have to log in with your browser go to Settings and I think pop/Imap and enable it there.

---

### Post by house055 on 2009-09-12
Yes, as I said in the first post. That I connect to imap.gmail.com over my home network, with my ipod, and two windows notebooks, as well as previously on this computer before I clean installed 9.04.

---

### Post by silverballer47 on 2009-09-18
Hmm, I wonder if it's an update that broke. I haven't had this problem before but as of six days ago, it has not been working. This is also when the first post was made...

If I had half a clue how to look this up, I would. I'm trying to go into aptitude's history and check to see if any SSL/TLS related packages were updated recently.

---

### Post by silverballer47 on 2009-09-18
Hmm, I wonder if it's an update that broke. I haven't had this problem before but as of six days ago, it has not been working. This is also when the first post was made...

If I had half a clue how to look this up, I would. I'm trying to go into aptitude's history and check to see if any SSL/TLS related packages were updated recently.

---

### Post by silverballer47 on 2009-09-18
And just as I posted, I'm finding that there are new updates to libssl...updating now. Maybe this will solve the issue?

*EDIT* No, same problem. For some reason I'm only having this trouble when I am on a wired Ethernet connection. Wireless works fine.

I'm also having connection troubles with anything that requires SSL/TLS, including GoogleTalk and VPNs...can one of the other people in this thread confirm? It might be a generic SSL issue. My sysadmin assures me that the firewall is not blocking anything.

---

### Post by house055 on 2009-09-20
Update...
I reinstalled 9.04 on my computer, installed all updates, and my email worked perfectly for 6 days until tonight. I am now getting the exact error messages I was before.

---

### Post by Rocket2DMn on 2009-09-20
I wonder if you are having DNS problems.  If you never changed anything and it suddenly stopped working, either something is wrong with the remote server, or DNS changed to direct to another server which isn't a gmail IMAP server.

---

### Post by ajmedfor on 2009-09-26
I just re-installed 9.04 and am having the identical problem. I haven't tried on a wireless connection yet though. Any new ideas?

---

### Post by ajmedfor on 2009-09-26
I also cannot connect to any other imap servers... I have tried all my school and work email accounts and get the same message. There was also something in the terminal output about XML Header Warning: Language not supported en-DK. I am currently living in Denmark, but my computer/install is in English... maybe being in a foreign country has something to do with it?

---

### Post by rygar on 2009-11-06
Same problem here, I'm getting the same errors from Evolution as in post #1 (haven't tried other clients).  Also, I can't get Google Talk working on empathy or pidgin, not sure if there's a connection.

I'm on a wireless network, running 9.10.

any ideas at all??

---

### Post by rygar on 2009-11-06
ahh i fixed it already!  been struggling since yesterday and finally fixed it 10 minutes after i post...

i had to disable moblock.  didn't think of it because i dont have a gui for moblock, so i didnt remember that i was running it!

anyway, i disabled moblock and it runs great, but im sure there's a way to create exceptions, so ill look into that...

hope this helps someone!

update: i re-started moblock, and imap still works!  just stopping and restarting seems to have fixed it, not sure what's going on exactly...

---

### Post by jre on 2009-11-09
If you are using moblock, you can add exceptions for ports or IPs in /etc/blockcontrol/blockcontrol.conf

E.g. to whitelist the whole outgoing imap port 993:
```
WHITE_TCP_OUT="993"
```

or in combination with http (80) and https (443):
```
WHITE_TCP_OUT="http https 993"
```

Or you can check /var/log/moblock.log for the IPs that were blocked and add them to WHITE_IP_OUT=""

Adding the IPs is a bit safer than allowing traffic on the whole port (to all IPs).


There are two explanations why restarting helped:
[LIST]
[*]After you ESTABLISHED a connection to the mail server, this connection was known - therefore it wasn´t checked any more, because only NEW connections are checked.
[*]Or the mail server changed its IP to another one, that doesn´t get blocked. I see Google changing those IPs quite often :-/
[/LIST]

---

### Post by Lunaryume on 2009-11-13
I just wanted to thank you for the suggestion to uninstall moblock. I have been searching the forums for a way to get Evolution or thunderbird to work for days, and this did the trick for me. Thank you!

---

### Post by thoth3g on 2009-12-10
Another suggestion for anybody having problems with using gmail Imap is to try Zimbra. In general gmail has been very slow on all of my installations windows and linux. Every mail client would have the same problems sending attachments for me. 
Zimbra has an installer so it's a breeze to install (.deb) and it has worked great for me. I have added all of my email addresses to the same in box using Zimbra.

---

