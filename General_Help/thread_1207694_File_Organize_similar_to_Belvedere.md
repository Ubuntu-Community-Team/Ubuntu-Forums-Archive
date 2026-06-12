---
title: "File Organize similar to Belvedere"
date: 2009-07-08
forum: General Help
---

### Post by kehon on 2009-07-08
is there a file organizer for ubuntu/linux similar to Belvedere for linux that automatically moves,deletes, files according to certain file properties like extension or file type, date created, date last modified, etc

---

### Post by wojox on 2009-07-08
Everything you just explained you can do with Nautilus.

---

### Post by kehon on 2009-07-08
yeah but i want it to be automated and if nautilus can do this can you explain

---

### Post by lukeiamyourfather on 2009-07-08
A shell script and cron could do it. Automatically deleting things based on file properties and extensions is playing with fire. Cheers!

---

### Post by kehon on 2009-07-08
probably not going to delete just mainly move

ps: just need something to organize my downloads folder and move compressed files to etc, exe to software, deb to software/linux etc how would i do this

---

### Post by kehon on 2009-07-08
thanks for this utility i didnt even know it was there i like it because now i have a way to make an animated gif but how would i split a gif image using this

---

### Post by benjaminoakes on 2011-06-22
I've created an open source, Belvedere/Hazel-inspired project that I'm calling "Maid". If you have RubyGems installed (typical if you have Ruby), it just takes a single command to install:

```
sudo gem install maid --pre
# And if you don't have RubyGems, this should set you straight:
# sudo apt-get install rubygems
```

Specifying --pre will install pre-release versions, the Maid release candidate version in this case.  The first stable release should be coming out within the next week, and I would love to have your input and opinions.

There's more info at [http://github.com/benjaminoakes/maid]("http://github.com/benjaminoakes/maid") and [http://rubygems.org/gems/maid]("http://rubygems.org/gems/maid")

Maid is based on some code I had written for myself. Eventually, it turned into something I thought others might find useful, so I packaged it up for others to use on Linux and the Mac.  I hope it's useful for you.

---

### Post by rickycodie on 2012-04-16
i downloaded and installed the files but i get an run error that says that there is no .maid/rules.rb flother than the obvious answer of "just make one" what can i do to get it to run?

---

