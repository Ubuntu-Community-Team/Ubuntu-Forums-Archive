---
title: "Losing icons when e-mailing"
date: 2012-06-11
forum: General Help
---

### Post by bencouve on 2012-06-11
I am trying to send e-mail's that have some images attached. When I receive the e-mail via Thunderbird the image is there, however, if I forward the e-mail on then the image is removed (just included this as it may be significant). Something like this arrives

[B][B]<strongoptimisation<             strong=""></strongoptimisation<>

[/B][/B]Also, the facebook and twitter icons disappear. 

What I actually want to do is send, via a script, group e-mails via the command line along with the company logo and the twitter and facebook images. 

If I type in the html code into the message, like this -

[FONT=Arial][SIZE=2]<P>[/SIZE][/FONT]
     [FONT=Arial][SIZE=2]<A href="[/SIZE][/FONT][[FONT=Arial][SIZE=2]http://www...."><IMG[/SIZE][/FONT]]("http://www.gomungoseo.co.uk%22%3E%3CIMG")[FONT=Arial][SIZE=2] border=0 src="[/SIZE][/FONT][[FONT=Arial][SIZE=2]http://www...../images/email-....-logo.jpg">[/SIZE][/FONT]]("http://www.gomungoseo.co.uk/images/email-go-mungo-seo-logo.jpg%22%3E")[FONT=Arial][SIZE=2]</A><BR>[/SIZE][/FONT][FONT=Arial][SIZE=2]<FONT[/SIZE][/FONT][FONT=Arial][SIZE=2]         color=#1a4267 size=3><STRONG>search         </STRONG></FONT><FONT color=#0099cc[/SIZE][/FONT]
     [FONT=Arial][SIZE=2]size=3><STRONG>engine         <FONT         color=#1a4267>optimisation</FONT><STRONG></FONT>[/SIZE][/FONT][FONT=Arial][SIZE=2]<STRONGOPTIMISATION<         STRONG></P>[/SIZE][/FONT]
     [FONT=Arial][SIZE=2]<P><A href="[/SIZE][/FONT][[FONT=Arial][SIZE=2]http://www.facebook.com/pages/..../137929989613785?sk=info"><IMG[/SIZE][/FONT]]("http://www.facebook.com/pages/Mungo-Design-Ltd/137929989613785?sk=info%22%3E%3CIMG")[FONT=Arial][SIZE=2] border=0 src="[/SIZE][/FONT][[FONT=Arial][SIZE=2]http://www...../images/email-facebook.jpg"></A>&nbsp;<A[/SIZE][/FONT]]("http://www.gomungoseo.co.uk/images/email-facebook.jpg%22%3E%3C/A%3E%C2%A0%3CA")[FONT=Arial][SIZE=2] href="[/SIZE][/FONT][[FONT=Arial][SIZE=2]http://twitter.com/gomungoseo"><IMG[/SIZE][/FONT]]("http://twitter.com/gomungoseo%22%3E%3CIMG")[FONT=Arial][SIZE=2] border=0 src="[/SIZE][/FONT][[FONT=Arial][SIZE=2]http://www......../images/email-twitter.jpg">[/SIZE][/FONT]]("http://www.gomungoseo.co.uk/images/email-twitter.jpg%22%3E")[FONT=Arial][SIZE=2]</A></P[/SIZE][/FONT][FONT=Arial][SIZE=2]>[/SIZE][/FONT]

 then I was expecting to see the images but only get the html stuff, as above. Can anyone advise on this. Here is the script I am testing, in its early stages. I installed postfix for this ..

#!/bin/sh

cat test_mail | awk '{print $1}' | while read LN ; do

printf "Subject: My Test\n\nHello\n\nThe text here ....with the html stuff ....\n " | sendmail -f me@company.[co.uk]("http://co.uk") $LN

done

 Any advice to keep the images in place would be greatly appreciated. 

P.S. Just in case of any worries, this is not spam mail but is being sent from a professional company to professional companies.

---

### Post by SeijiSensei on 2012-06-11
First, if you point to remote URLs to show the images, many of us will never see them.  Most of the time remote image URLs are used to identify whether a person actually viewed an email and thus constitute a privacy violation.  My version of Thunderbird routinely suppresses those images and displays a "show remote images" button when such messages arrive.  Some mail scanning software like [MailScanner](http://www.mailscanner.info/) will tag and suppress such images by default.

So the best alternative is to generate a MIME-encoded email with the images included as part of the message.  I recommend composing a template message in the Thunderbird HTML editor with the images embedded in the message.  Now look at the message source, and you'll see how the images are converted to MIME and linked by reference into the message text.  You'll see that there is also a plain-text version of the content along with the HTML-encoded material.  Obviously the plain-text version won't have any embedded images.

---

### Post by bencouve on 2012-06-11
Thanks for your repsonse. The thing is I just included thunderbird in my question as I noticed it had removed the images on forwarding. I actually want to include the images in my shell script, if possible. Can I put the MIME-encoding in a shell script? 

However, I will research the MIME-encoding now.

---

### Post by SeijiSensei on 2012-06-11
I'd create a template message with placeholders for any variable fields, then have the script read the template, replace the placeholders, and pipe the result to mail.  I take it you have a list of recipients to whom you wish to send the message.

So in broad terms the script might look something like:

```

#!/bin/bash

# get list of recipients
TO=$(cat /path/to/recipient_list)

for a in $TO
do
   sed "s/%RECIPIENT%/$a/g" < /path/to/template | mail -s 'An exciting new message for you' $a
done

```

where the template has the string "%RECIPIENT%" in the To: field.

I don't see any reason to compose each message on-the-fly in the script.  It's much easier to store the template message in a file and use the script to generate the individualized messages and mail them out.

If the recipient list has both the full name and email address for each person, (e.g., "Seiji Sensei <seijisensei@example.com>") you'll need to encase the "$a" at the end of the mail command in double-quotes:

```
sed "s/%RECIPIENT%/$a/g" < /path/to/template | mail -s 'An exciting new message for you' "$a"
```

---

### Post by bencouve on 2012-06-11
That looks very useful. Thank you.

---

### Post by bencouve on 2012-06-12
Sorry to raise this again but after the brilliant suggestion, which, incidentally has been applied, there is another thing to deal with.

[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"), the template idea is great, however, when the e-mails arrive there is an issue with the To: address being something like

"$a@ben"@thecompany.com

Something like that. Would you be able to suggest how I get rid of this? Thanks in advance. I need the client address to appear here for obvious reasons. And @thecompany.com is my our company and not the domain where we are sending. The $a@ben must be coming from the script but my prompt reads 

 ben@ben-desk-top:~/directory$

---

### Post by SeijiSensei on 2012-06-12
Ah, my bad. I put the sed command inside single quotes which makes bash treat $a as a literal rather than as an environment variable.  Try this:

```
sed "s/%RECIPIENT%/$a/g" < /path/to/template | mail -s 'An exciting new message for you' "$a"
```

When double-quotes are used, bash replaces any variables it finds with their values.  With single quotes, it treats variables as literal strings.  In most cases when I'm using sed, I'm replacing a fixed string with another fixed string, so I customarily use single quotes.  Force of habit won out in this case.

Once you've fixed this, the @mycompany.com problem should go away.

I've fixed the original post above as well.

---

### Post by bencouve on 2012-06-12
You are a serious guru. I will try that. Thanks

---

### Post by bencouve on 2012-06-12
Ye, that works great. It's just the other request now :)

---

### Post by SeijiSensei on 2012-06-12
> **bencouve said:**
> Ye, that works great. It's just the other request now :)

What's that again?

---

