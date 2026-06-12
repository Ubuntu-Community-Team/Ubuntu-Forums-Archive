---
title: "unattended-upgrades: Changing the mail Subject"
date: 2010-04-07
forum: General Help
---

### Post by deracled on 2010-04-07
I'm using unattended-upgrades on some servers that are configured to send email with the same from address (to be able to handle bounces better) 

sending address is something like [EMAIL="root@internaldomain.com"]root@internaldomain.com[/EMAIL] so I use the subject of the email to know what server the email was send from.
Other programs like logwatch do that without any configuration change but with the "unattended-upgrades" package I did not find a way to do that and all emails seem to come from the same source although you can find who the sender is by looking into the email headers but that's not very useful. 

This is what the subject looks like:
Subject: unattended-upgrades result
What I would like to have is something like this:

Subject: hostname: unattended-upgrades result 
Can anyone help out on this?

Thanks 
Doro

---

