---
title: "Groupwise 7 and Java-6 Update"
date: 2009-09-10
forum: General Help
---

### Post by rwigle on 2009-09-10
Last night, I did the recommended update of Java-6 to 1.6.0_16 (Hardy Heron). Now Groupwise 7 no longer works on that machine.

I tried to do the "obvious" thing of revising the old "jre" link to the new one, but I could not get that working. (For those of you who have done this install this probably makes sense.)

I saw a web page talking about installing Groupwise 8 (seems relatively painless).

[http://blog.icepick.co.za/index.php/2008/04/04/getting-novell-groupwise-to-work-in-ubuntu/]("http://blog.icepick.co.za/index.php/2008/04/04/getting-novell-groupwise-to-work-in-ubuntu/")

My questions are:

1. Does anyone have Groupwise 7 working after the sun-java6 update?

2. Any comments on installing Groupwise 8 under Ubuntu.?

I am holding off updating java-6 on another machine until I sort this out.

---

### Post by rwigle on 2009-09-16
It appears that when sun-java6 was updated to 1.6.0.16, I messed up refreshing groupwise's link to jre.

Should have done (as root):

```

rm -R /opt/novell/groupwise/client/jre
ln -s /usr/lib/jvm/java-6-sun-1.6.0.16/jre /opt/novell/groupwise/client/jre
ln -s /usr/lib/jvm/java-6-sun-1.6.0.16/jre /usr/lib/jre
```

Now Groupwise 7 is working as before.

---

