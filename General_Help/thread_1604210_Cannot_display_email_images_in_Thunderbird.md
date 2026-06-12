---
title: "Cannot display email images in Thunderbird"
date: 2010-10-23
forum: General Help
---

### Post by Tony_Harrison on 2010-10-23
Hi All:

I'm running TB 3.1.5. Images do not display in emails. There is no "Display Images" button. Where the images would be, I only get a broke image icon (the little torn page). 

I don't know if this is a Ubuntu specific issue, but I thought I'd post here because the community is so responsive.  

Any ideas would be very welcome.

P.S. I have tried the solution at this site, but though the mail.default_html_action value is set to 3, I still have no luck.
[http://community.contractwebdevelopment.com/images-missing-thunderbird]("http://community.contractwebdevelopment.com/images-missing-thunderbird")

---

### Post by SeijiSensei on 2010-10-23
First, have you permitted remote sites to send you image files?  In general, this is a very bad idea.  Marketers include images so they can track that your email address is reachable and that you've seen their message.  So Thunderbird asks you if you want to display "remote content" from other sites; just be judicious in what you choose to accept.  Thunderbird will ask if you want to accept images from senders automatically by placing them in your Address Book. For senders you trust, this is the easiest solution.

As for attached images, perhaps you don't have a default program defined for images?  I use Kubuntu where Gwenview is the default viewer; in standard GNOME Ubuntu there's "Eye of GNOME".  If you right-click on an attached PNG or JPEG, what are the "Open with" options?  What happens if you just pick "Open"?  On my Kubuntu 10.10 machine choosing "Open" opens "display" which uses ImageMagick to show the graphic in a separate window.

---

### Post by Tony_Harrison on 2010-10-23
Here is a pic of what I am seeing:
[IMG]http://farm2.static.flickr.com/1152/5108284459_8915913fa4_m.jpg[/IMG] But when I right click on it I get the same Context Menu as I would clicking anywhere in the email's body. It mentions nothing about opening the image.

Just to clarify, these images are not attachments, they are indeed embedded in the message. I understand the security implications of accepting images.

---

### Post by SeijiSensei on 2010-10-26
> **Tony_Harrison said:**
> Here is a pic of what I am seeing:
[IMG]http://farm2.static.flickr.com/1152/5108284459_8915913fa4_m.jpg[/IMG] But when I right click on it I get the same Context Menu as I would clicking anywhere in the email's body. It mentions nothing about opening the image.

Just to clarify, these images are not attachments, they are indeed embedded in the message. I understand the security implications of accepting images.

That's the placeholder Thunderbird uses when it has blocked remote images from displaying.  When you have that image, don't you also have a blue bar with the "Show Remote Content" button?  You should also see an "Always load remote content from [email]someone@example.com[/email]" link in that bar as well.   Clicking the button displays the remote content on a one-time-only basis.  The "always load" method adds the sender to your Address Book which means all images from that sender will be displayed inline automatically.

Go to Help > About.  What version of Thunderbird is this?

---

### Post by Tony_Harrison on 2010-10-26
I do not have said blue bar. I remember having it in previous versions of TB. I am currently running Thunderbird 3.1.5.

---

### Post by SeijiSensei on 2010-10-27
> **Tony_Harrison said:**
> I do not have said blue bar. I remember having it in previous versions of TB. I am currently running Thunderbird 3.1.5.

I'm running 3.1.5 and always see the blue bar when I get unsolicited messages with embedded graphics.  Check to see if the message sender is in your address book.  Then you wouldn't get the blue bar, but you should then also see the inline graphics.  The only time that wouldn't work is if your connection is down, you're working offline, or the server that distributes the sender's images is down. 

I'd suggest asking this in the [Thunderbird forum]("http://getsatisfaction.com/mozilla_messaging/products/mozilla_thunderbird"); perhaps others have this issue as well.

---

### Post by Tony_Harrison on 2010-10-28
I'm not entirely sure what resolved the problem, but here is a list of things I did and now it works:
View->Message Body As->Original HTML (was Simple HTML)
View->Headers->All (was Normal)
   I then switched it back to Normal.
Also, I followed all of the instruction at this page
[http://community.contractwebdevelopment.com/images-missing-thunderbird ]("http://community.contractwebdevelopment.com/images-missing-thunderbird")

What ever it was (I strongly suspect it was the Message Body As HTML->Normal) it works now!

BTW : My bar is black, not blue.

Thanks for all your help, SeijiSensei. I call this one solved!

---

