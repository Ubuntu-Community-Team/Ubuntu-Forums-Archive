---
title: "Gallery - Opinions?"
date: 2010-04-08
forum: General Help
---

### Post by gunksta on 2010-04-08
Between myself and my girlfriend, we have too many computers in the house. I already have a plan to centralize the music/video onto a single computer. I'd like to do the same with the pictures. Right now she uses her file-system to sort/organize her photos and I tend to use tags (digikam/f-spot).

Digikam and f-spot seem to be stuck in the "single-user" mindset of the late 20th century  :popcorn:  and do not make it easy to share collections/databases. I want to set up ONE photo management system that we both upload pictures to. Photo editing (Gimp, Hugin, etc.) will still be done on client machines. I want something like f-spot/digikam that is capable of creating/indexing tags but I want it to be on the network and not stuck on a single machine.

I looked through the repos and found [Gallery]("http://gallery.menalto.com/"). Does anyone here have any experience with Gallery? Will it meet my needs? It can do albums (which is good for my girlfriend) but i can't see if it does tags or not. I do like how I would be able to browse/upload photos from any computer on the network.

Does anyone have any opinions/experience with Gallery or experience with another similar solution/tool. Access via a browser is not a requirement. If I need to set up a client/program on each machine, that is fine -- provided they all share a single database.

[COLOR=Silver] Now that i think about it -- a desktopcouch type system would be neat here, but such a solution is beyond me at the moment. Alternatively, I suppose it would be possible to do this via desktopcouch/f-spot by symlinking the database and photos into the Ubuntu One folder, but I have WAY more than 2 GBs of photos and I haven't decided yet if I'm going to pay for that yet.
[COLOR=Black]After thinking about this some more I have decided that a desktopcouch solution is NOT what I am looking for. I don't want this thread to get distracted by that idea. I would prefer to focus on [Gallery]("http://gallery.menalto.com/")[COLOR=Silver] [COLOR=Black]or program similar to it.[/COLOR][/COLOR][/COLOR]
[/COLOR]

---

### Post by gunksta on 2010-04-08
I just thought of another possible problem in using a couchdb approach. Ubuntu One currently assumes you are sharing files with yourself. But it is conceivable that if I shared the F-Spot database between multiple computers via Ubuntu One that we could both be editing the database at the same time and it would be impossible/difficult to merge the two changes together and I don't know if Ubuntu One even has the ability to flag and warn you about this possibility.

I think I want to keep my photos on my home network only. I don't want to involve something like DropBox or Ubuntu One.

And, I think I want to stick to a boring, SQL based approach.

But, I do want to access the files from several different computers.

---

### Post by mcduck on 2010-04-08
Maybe there's some PHP/MySQl-based web gallery that has the required features? You could set up Apache and run the gallery locally on your own computer/LAN..

---

### Post by gunksta on 2010-04-08
> **mcduck said:**
> Maybe there's some PHP/MySQl-based web gallery that has the required features? You could set up Apache and run the gallery locally on your own computer/LAN..

There is a PHP/MySQL based web gallery -- and it's called [Gallery]("http://gallery.menalto.com/") and it's in the repos.

[http://gallery.menalto.com/](http://gallery.menalto.com/)

I said as much in my OP, but I did go back and include the link when I mentioned [Gallery]("http://gallery.menalto.com/"), to make it clearer. Based on what I can find with my apt-cache search skills, I think it is the only such tool in the Ubuntu repos. I am hoping someone here has some experience with Gallery and can tell me if it's worth installing/setting up.

---

### Post by gunksta on 2010-04-08
After looking at the documentation some more, and the names of the modules for Gallery3, it looks like it can definitely do tags. For example, it has a module to let it create a tag cloud (cool idea) and thus I assume it be used to edit tags and such.

Very cool.

I guess at this point I'm just looking to see if anyone has installed and used Gallery. The examples I see on the 'Net look incredible but I'd like to get some less biased, first hand experience/beta.

---

