---
title: "vlc - codecs"
date: 2011-02-16
forum: General Help
---

### Post by ddjolley on 2011-02-16
I installed VLC.  Nice.  Played everything I could think of to through at it out of the box.

After completing the installation I did a "dpkg --get-selections | grep gstreamer".  I was expecting to see gstreamer0.10-plugins-bad.  I didn't.  My question is: What codecs does vlc use out of the box?  What do I need to do to replace those with the Fluendo codecs which I own?

Thanks for any input.

          ... doug

---

### Post by ddjolley on 2011-02-16
I have since learned that VLC has its own codecs.  So, that explains why I didn't see gstreamer0.10-plugins-bad.  In light of this new information, my question becomes:  How do I remove from VLC the stock codecs that it ships with and substitute the Fluendo codecs?  Thanks.

        ... doug

---

### Post by blueridgedog on 2011-02-16
I would search or post here:

[http://forum.videolan.org/](http://forum.videolan.org/)

---

### Post by ddjolley on 2011-02-17
> I would search or post here:

[> http://forum.videolan.org/]("http://forum.videolan.org/")

I followed your suggestion and posted my question to that forum.  For the record, the response that I got back indicated that it is not possible to use the Fluendo codecs with VLC.  That's disappointing.  I really like VLC; but, for this particular project, I need a desktop installation that is beyond reproach.

Thanks for your input.

        ... doug

---

### Post by blueridgedog on 2011-02-17
I did a search as well and the only option I found was to add your codec at compile time, which is a complex solution.

---

### Post by sydbat on 2011-02-17
> **ddjolley said:**
> > I would search or post here:

[> http://forum.videolan.org/]("http://forum.videolan.org/")

I followed your suggestion and posted my question to that forum.  For the record, the response that I got back indicated that it is not possible to use the Fluendo codecs with VLC.  That's disappointing.  I really like VLC; but, for this particular project, I need a desktop installation that is beyond reproach.

Thanks for your input.

        ... dougVLC **is** beyond reproach. Everything included is completely legal.

---

### Post by colin.p on 2011-02-17
I'm sorry but I can't for the life of me figure out why on earth you would want to remove perfectly fine codecs and replace them with others.
I know that the Fluendo codecs are a "for sale" product and you would want to use something that you paid for, but still...

---

### Post by ddjolley on 2011-02-21
> VLC **is** beyond reproach. Everything included is completely legal.

OK.  Technically you are correct in that the VLC package itself is as pure as the driven snow.  However, in order to satisfy some dependencies, the VLC package requires some other packages that are not so pure.  That's where the "reproach" comes in.

> I'm sorry but I can't for the life of me figure out why on earth you would want to remove
> perfectly fine codecs and replace them with others.

When you say, "perfectly fine codecs" I think what  you mean is codecs that are "perfectly fine" in terms of functionality.  While the codecs we are talking about are "perfectly fine" functionally, there are many that believe that using them in certain jurisdictions constitutes a violation of the law.  It is for that reason that I want to replace the existing codecs with codecs that are not tainted with any possible legal issues.

Thanks to all for the input.

            ... doug

---

### Post by sydbat on 2011-02-22
> **ddjolley said:**
> > VLC **is** beyond reproach. Everything included is completely legal.

OK.  Technically you are correct in that the VLC package itself is as pure as the driven snow.  However, in order to satisfy some dependencies, the VLC package requires some other packages that are not so pure.  That's where the "reproach" comes in.

> I'm sorry but I can't for the life of me figure out why on earth you would want to remove
> perfectly fine codecs and replace them with others.

When you say, "perfectly fine codecs" I think what  you mean is codecs that are "perfectly fine" in terms of functionality.  While the codecs we are talking about are "perfectly fine" functionally, **there are many that believe that using them in certain jurisdictions constitutes a violation of the law**.  It is for that reason that I want to replace the existing codecs with codecs that are not tainted with any possible legal issues.

Thanks to all for the input.

            ... dougUm...you are worried about absolutely nothing. You say you bought the Fluendo package. Therefore, any codecs that come with an application are covered under whatever nebulous, US only "legality" you are stressing about.

The "codec police" are not going to knock down your door and arrest you because you did not "*replace the existing codecs with codecs that are not tainted with any possible legal issues*".

---

