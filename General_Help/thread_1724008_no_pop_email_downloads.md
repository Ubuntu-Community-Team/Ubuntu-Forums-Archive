---
title: "no pop email downloads"
date: 2011-04-07
forum: General Help
---

### Post by jwlacy72 on 2011-04-07
I have ubuntu 10.10 and thunderbird 3.1.9.  thunderbird will not download messages from any pop server, it just states no messages to download.  I log into the web version of either pop server and there are hundreds of messages.  I have so far deleted both po account settings and put them back, tried both ssl and not ssl, unchecked leave messages on server, removed and reinstalled thunderbird.  any help would be appreciated

---

### Post by SeijiSensei on 2011-04-08
Try an experiment from the command prompt like this (replacing "pop3.example.com" with the actual name of your POP3 server and "username" and "password" with their actual values):

```

telnet pop3.example.com 110
[server replies with banner]
user username
[server replies OK]
pass password
[server replies OK]
list
[server replies with number of messages]
retr 1
[server displays message #1]
quit

```

If that works, then I don't know what Thunderbird's problem might be.  I suspect there's a connectivity issue of some type involved.

Here's a quick overview of the [POP3 commands]("http://www.electrictoolbox.com/article/networking/pop3-commands/") you can use in this experiment.

If the provider supports IMAP as well as POP3, use IMAP instead. It's a much better protocol, especially if you'll be reading your mail with different clients like TBird locally and the webmail client you mention.

---

### Post by jwlacy72 on 2011-04-08
pop server responded perfectly to the commands given.

imap is not an option the company hosting our mail does not support imap.

so if thunderbird is my culprit does anyone have any suggestions?

---

### Post by SeijiSensei on 2011-04-08
Hmm.  With TBird closed, run "mv .thunderbird .thunderbird.bad" in your home directory, then open TBird to force it to create a brand-new profile.  Does that help?

---

### Post by jwlacy72 on 2011-04-11
Creating a new profile has no effect.  The new profile shows "no messages to download" as well.  Over the weekend I set up evolution as a test and evolution will not download messages as well, but evolution times out instead of showing no messages to download.

---

