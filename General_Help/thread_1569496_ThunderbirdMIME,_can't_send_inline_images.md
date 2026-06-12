---
title: "Thunderbird/MIME, can't send inline images"
date: 2010-09-06
forum: General Help
---

### Post by rslee on 2010-09-06
I don't think this is actually an Ubuntu issue; but after hours of searching I can't find an answer to what seems like a fairly simple question.  So I figure there's a slim chance it's platform-related.  At the very least, you guys will be able to tell me where I really should be looking.

I'm trying to send HTML email with local, inline images that don't get blocked by standard mail readers.  From what I understand, if I send the images with the email, with Content-disposition:inline, this should work.

I'm sending the test messages to a Gmail account and a Yahoo! Mail account.  The Gmail account gives me the usual "Display images below" message and shows the images as attachments at the end of the message. Yahoo actually says "To protect your privacy, Yahoo! Mail has blocked remote images in this message."  But there are no remote images in the message!  Just below the headers, the two images are listed as attachments.

I have verified that the Content-disposition for both images is inline.  I also have, in the Gmail account, two messages from untrusted senders with images in the signature that display without a hitch and are not shown as attachments (one X-Mailer is Outlook and the other Apple Mail).  Is Thunderbird the problem?  Where can I find an explanation of how all of this works?

I'm using Lucid Lynx 64-bit and Thunderbird 3.0.6.

Thanks!

---

