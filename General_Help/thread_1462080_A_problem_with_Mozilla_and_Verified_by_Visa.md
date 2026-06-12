---
title: "A problem with Mozilla and Verified by Visa"
date: 2010-04-25
forum: General Help
---

### Post by Extreedoc on 2010-04-25
Hi all,

I've had Ubuntu for about a year now and had no serious issues and am loving it, however a problem has cropped up: I shop online with Tesco and Verified by Visa and lately after ages of trouble free shopping I now have Visa saying that the password we use is not accepted even though I know it is correct. Been in touch with V by V and they have identified a problem with Mozilla and recommend changing to Google Chrome. This I do not want to do, any ideas?
PS, I am still running Intrepid

---

### Post by SnickerSnack on 2010-04-25
Use another browser just for that purpose.  You don't need to switch to chrome (or opera...) completely.

---

### Post by mick222 on 2010-04-25
If it's a bug in firefox you can check here and report it if need be [https://bugzilla.mozilla.org/](https://bugzilla.mozilla.org/)

---

### Post by Untitled_No4 on 2010-04-25
That's a bit cheeky of them to tell you that. What would they say if you told them you spoke to Mozilla and they recommended using MasterCard?

Last time I had to use verified by visa if I clicked cancel on their screen the transaction still went through. It's actually what they told me to do when I had issues in the past since they said it's not compulsory and that they know they have issues with Firefox.

---

### Post by Extreedoc on 2010-04-25
> **Untitled_No4 said:**
> That's a bit cheeky of them to tell you that. What would they say if you told them you spoke to Mozilla and they recommended using MasterCard? 

I like the way you think, maybe I'll put that to them??

> **Untitled_No4 said:**
>  Last time I had to use verified by visa if I clicked cancel on their screen the transaction still went through. It's actually what they told me to do when I had issues in the past since they said it's not compulsory and that they know they have issues with Firefox.

Did you have the same issue then, and did you have no problems until recently?

---

### Post by Untitled_No4 on 2010-05-02
Sorry for the late reply.
Yesterday I bought something online and was directed to the verified by Visa screen again and it worked. I did have the issue but that was quite some time ago and I think it only happened on one computer, which leads me to think there might be something in the cache or addons that causes the problem rather than it being a Firefox specific problem.

The first thing I'd try doing is to rename ~/.mozilla folder and restart Firefox and test. Firefox will create a new clean ~/.mozilla without your cache and without some of your addons (if you have any).

If it still doesn't work try disabling the addons that are still in use and test again. 

If you want to revert from your test you only need to delete the newly created .mozilla folder and rename the previous folder back to .mozilla and all your settings, history and addons will be there again. 

If all fails, try clicking on Cancel (or whatever they have there) on the Verified by Visa screen as it might still not be compulsory.

---

