---
title: "ending an unruly process"
date: 2010-12-19
forum: General Help
---

### Post by jaminb on 2010-12-19
This problem seems almost impossible as I think I have ended all the processes necessary to make this work. I'll start from the beginning. I am way from the house alot and I wted to be able to moniter the screen of my computer from my cell phone. To do this I wrote two different scripts, a screencapture script which took ha 5 second capure and converted it into a .gif, and an email script which would then email me this capture using mutt. I then installed crontab which would execute the scripts every hour. I then rigged up the filters in my gmail account to forw the emailsto my cello hI could view them via sms. I thought it would work but for no apparent reason it began to send me 30 to 40 emails a minute. Essentually I was Ddos attacking myself. I deleted the script uninstalled crontab and mutt, and deleted the two scripts. I rebooted but I am still recieving the emails..... when I look at the proces there is still .sh proces running but even when I ended it the emails still come. How is this possible and how can I fix this. Thanks.

---

### Post by techunit on 2010-12-19
Turn off the computer... problem solved.

How are you accessing the computer or do you still have access. Can you create a filter to delete the messages in gmail? Honestly just restarting the computer should do it because the processes sound as though they shouldn't restart if they can't be excuted. Good luck... Um you could have just used VLC or a SH connection through your smart phone far more practical.

---

### Post by tgalati4 on 2010-12-19
That's a funny story.  I modified my home alarm to call my cell phone when it encountered trouble codes.  Nothing like getting woken up at 4:30 in the morning for a power outage.

My guess is that your mail queue was stuffed with email just waiting to get sent out.  Since the mail handler is always working, it would just keep sending out, even though you killed several processes.  Mail handlers are designed to keep sending mail.  That's what they do.  And they are good at it.

What exactly are you trying to accomplish?  There must to be a more elegant way to do it than screen capture.

---

### Post by jaminb on 2010-12-19
restarting doesnt work the process runs from start up. Of corse turning  off my computer ends the process but this  is hardly a permanent fix. I thoght it was a mail queu problem but I dont get emails if I shut down the computer. I would use ssh but I dont have a smartphone...sorry about the spelling Im typing from a phone keyboard.

---

