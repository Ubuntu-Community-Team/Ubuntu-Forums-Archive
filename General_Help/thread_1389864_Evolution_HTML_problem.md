---
title: "Evolution HTML problem"
date: 2010-01-24
forum: General Help
---

### Post by yester64 on 2010-01-24
Hi, somehow i have problems to send html message with included pictures. These are small pictures (around 200K) and if i check in the outbox the pictures are striped away.
How? Is there something i overlooked?

---

### Post by howefield on 2010-01-25
> **yester64 said:**
> Hi, somehow i have problems to send html message with included pictures. These are small pictures (around 200K) and if i check in the outbox the pictures are striped away.
How? Is there something i overlooked?

Do the recipients see the pictures as intended, or do they see the same as you.

---

### Post by yester64 on 2010-01-25
> **howefield said:**
> Do the recipients see the pictures as intended, or do they see the same as you.

No, no pictures are sent and no pictures are in the original message.
If i send it as a text message and attach it, pictures get sent.
But i really would like to send it as a HTML mail and paste the pictures.
Not sure if Evolution perhaps just filters the images out before the get send.

---

### Post by howefield on 2010-01-25
I tend to send and receive in plain text and send pictures as file attachments, and only use html by exception, so I'm not sure, but you could try going into the Edit > Preferences menu, select Composer Preferences and place a check beside Format messages in HTML.

See if that helps.

---

### Post by Lefuneste on 2010-02-20
I have the same terribly annoying problem with Evolution under Ubuntu 9.10. 
Inserted pictures in HTML outgoing emails get stripped out and do not appear anymore when editing sent message, or in the recipient inbox. The picture itself is stripped out of the mail when sending and never exits the computer. If the picture is added as a joined file it works fine, but not as a picture added to an HTML formatted message. What the F... is going on here... This is a nightmare. I've checked all settings, reinstalled Evolution, nothing works. I have moved to Thunderbird on the same system and it works perfectly... Any idea of where to look at to solve this bug?

---

### Post by Lefuneste on 2010-02-20
Problem due to RSS plugin

[https://bugs.launchpad.net/evolution/+bug/51116](https://bugs.launchpad.net/evolution/+bug/51116)

---

### Post by dcstar on 2010-02-21
> **Lefuneste said:**
> Problem due to RSS plugin

[https://bugs.launchpad.net/evolution/+bug/51116](https://bugs.launchpad.net/evolution/+bug/51116)

No wonder a lot of people do not have this problem (like me), not everyone installs that plugin.

---

### Post by barretr on 2010-02-25
You can patch the RSS plugin to work with inline images by following the steps in this thread: [http://ubuntuforums.org/showthread.php?t=1380925#7](http://ubuntuforums.org/showthread.php?t=1380925#7).

---

