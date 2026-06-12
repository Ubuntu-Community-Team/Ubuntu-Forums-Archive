---
title: "Can't successfully insert images into Evolution"
date: 2010-06-12
forum: General Help
---

### Post by Subito Piano on 2010-06-12
Hi!  Using Ubuntu 10 (Ubuntu Studio) with Evolution 2.28.3 - i can LOAD images into Evolution and they appear while i compose the email but they do NOT appear in the recipient's email --  they do not appear even if i send an email to myself!  I DO have "format messages in html" checked.   I DO NOT have "always load images from the internet" checked because that refers to my inbox, not to me composing an email; instead, i have "load images in messages from contacts" checked; besides, these are local pictures that i am inserting, not from the web.  Again, neither a friend can see the images (though she can when receiving them from other ppl) nor can i see them if sent to myself, or even in my copies in my "sent mail" folder.  The emoticons behave similarly.  Is this a glitch?

I am new to Evolution, though quite familiar with Linux and with T-bird, K-Mail, Claws, etc.

Any help would be appreciated.

---

### Post by dcstar on 2010-06-12
> **Subito Piano said:**
> Hi!  Using Ubuntu 10 (Ubuntu Studio) with Evolution 2.28.3 - i can LOAD images into Evolution and they appear while i compose the email but they do NOT appear in the recipient's email --  they do not appear even if i send an email to myself!  I DO have "format messages in html" checked.   I DO NOT have "always load images from the internet" checked because that refers to my inbox, not to me composing an email; instead, i have "load images in messages from contacts" checked; besides, these are local pictures that i am inserting, not from the web.  Again, neither a friend can see the images (though she can when receiving them from other ppl) nor can i see them if sent to myself, or even in my copies in my "sent mail" folder.  The emoticons behave similarly.  Is this a glitch?

I am new to Evolution, though quite familiar with Linux and with T-bird, K-Mail, Claws, etc.

Any help would be appreciated.

Works fine on my system.

---

### Post by Subito Piano on 2010-06-13
Well, umm...yeah, but it's not working on mine -- i need some ideas! :(

---

### Post by Subito Piano on 2010-06-27
Hmm -- two weeks...either i'm alone in this (i know that's not true) or everyone who has such a problem hasn't found the cure?

---

### Post by Subito Piano on 2010-06-30
well -- i finally found the answer to my own question.  Long and short of it, either diable the RSS plugin (which i did) or download the file evolution-rss-0.1.4 (which i did NOT try, inasmuch as it's not a deb package and i don't wanna bother looking up what to do with the tarball or RPM file.  
Bug report [here]("https://bugs.launchpad.net/evolution/+bug/51116") and [here]("https://bugzilla.gnome.org/show_bug.cgi?id=341258") 
Tarball and RPM of replacement evolution-rss-0.1.4 [here]("http://linux.softpedia.com/progDownload/evolution-rss-Download-26268.html") (but compare [here]("https://launchpad.net/ubuntu/lucid/+source/evolution-rss/0.1.4-6ubuntu0.1")) 
they have a deb patch almost ready -- [here]("https://bugs.launchpad.net/ubuntu/+source/evolution-rss/+bug/452874") 

Hope this helps someone else!

---

### Post by dcstar on 2010-07-01
> **Subito Piano said:**
> well -- i finally found the answer to my own question.  Long and short of it, either diable the RSS plugin (which i did)
.........
Hope this helps someone else!

Non-default Evolution plugins seem to cause massive problems on an ongoing basis.

People keep installing them, then complain that they have ongoing Evolution problems when all the others who don't play with these things do not experience any issues at all.

You don't have to look far in the forums to find people who continually bag Evolution saying that "it never works" when the problem is probably these additional plugins that are created by 3rd parties and the Evolution developers have little control over them.

---

### Post by Subito Piano on 2010-07-01
...meaning i should pass this along to the Ubuntu Studio folks, inasmuch as it was installed by default....  :roll:

---

