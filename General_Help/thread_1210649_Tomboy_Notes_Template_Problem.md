---
title: "Tomboy Notes Template Problem"
date: 2009-07-11
forum: General Help
---

### Post by american.white.pelican on 2009-07-11
Hi,
I'm new to the Ubuntu community, and have been enjoying getting used to my new favorite OS. I recently discovered Tomboy Notes. I wanted to change the default template so I didn't have to always delete the basic text that said "Type your title here" "Type your note here" etc.

But...when I tried to go into the default template, I got an error message saying, 

An error occurred while loading or saving configuration information for tomboy. Some of your configuration settings may not work properly.

Bad key or directory name: "/desktop/gnome/url-handlers/": Key/directory may not end with a slash '/'

How can I fix this and let Tomboy simply give me a blank page as my default note template?

I had deleted both the welcome notes that described how to use Tomboy, but I'm not sure if that should have caused such a problem with the program as this. If anyone has the time to give me a little advice on what to do here, I'm very thankful!

John

---

### Post by villalcalde84 on 2009-07-11
I have used Tomboy for some time now, and I really like it, but having to delete the messages that indicates where to write the title and text everytime I create a new note is a little annoying.

I would like to know how to create a blank template too. If anyone knows how to do this, it would be really helpful.

Thaks in advance.

---

### Post by Mark20 on 2009-07-31
EDIT:
The new version of Tomboy fixes this issue, download it here: [http://projects.gnome.org/tomboy/download.html]("http://projects.gnome.org/tomboy/download.html")


Hey,

The template problem is a bug which has been fixed in Tomboy version 0.15.2 and forward.  Unfortunately the Tomboy website only has prebuilt binaries up to 0.15.1 :(.  0.15.2 binaries will be coming out soon, but in the meantime you will need to checkout and build the source so you can get a version of Tomboy with the fix for templates.  Not sure how familiar you are with building source, but in this case it's actually very easy:

```

sudo apt-get install git-core
git clone git://git.gnome.org/tomboy
sudo apt-get build-dep tomboy
cd tomboy
./autogen.sh --disable-scrollkeeper
make
make install

```

Cheers,
Mark

---

### Post by nac.est on 2011-01-05
This is a really old thread, but I still can't manage to get a blank template on Tomboy 1.4.2.
I open the options window, go to the Edit tab and click on "Open new template". A note comes up, but if I simply delete everything in it, the next time I open a note it's the same as before.
Am I doing something wrong?

---

### Post by strandlooper on 2011-08-15
I like Tomboy. Two things I don't like. I would like to change the color of the [COLOR="Yellow"]icon[/COLOR] and to have a blank template. Would be great get help.

---

