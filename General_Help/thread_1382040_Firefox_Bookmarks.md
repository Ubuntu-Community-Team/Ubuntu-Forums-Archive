---
title: "Firefox Bookmarks"
date: 2010-01-15
forum: General Help
---

### Post by dmcdaniel on 2010-01-15
Hello Everyone,

Done much searching and haven't been able to find anything to do what I need it to so far. 

What I need to do:

Share Firefox bookmarks with multiple pc's on a network. I need them to be uneditable and easy to update.

Idea: Place the Firefox profile on one Server pc and make it a shared file. Make the other pc's look at that Firefox's profile location and use that profile as startup (I would do chmod 755 to keep it from being edited).

Problem: When I do this, it I can only open it on one pc at a time. Is there a way to get around this? If so, How?

---

### Post by iMisspell on 2010-01-15
> **dmcdaniel said:**
> Problem: When I do this, it I can only open it on one pc at a time. Is there a way to get around this? If so, How?
In recent versions of Firefox, thats how it is. Never really looked too deep into it, but it seams when Firefox opens, it will move our bookmarks to memory or a temp location, once Firefox is closed it will then save to the default location. So you can not share across machines any more.

If you search (for 'bookmark') in Firefox's Extensions site, there are extensions which will do what you want, you have to do a little configuring, but it can be done, just not with Firefox's current default bookmarking system. You have to use an extension or create your own bookmarking system.

Theres alot of info in yahoo or google about this.

---

### Post by gdonwallace on 2010-01-15
You might try permissions of 766, that should give read and write across the board.

I would also suggest using the add-on xmarks.  It makes a backup of your bookmarks, as long as you have that installed on all the machines and have them sync up on the first time, each machine will have the same bookmarks and if anything changes, you can resync a second time for each machine and it will pick up the changes.

---

### Post by dmcdaniel on 2010-01-15
Thanks for the responses. 

I have tried xmarks - the problem is - it syncs any new bookmarks. I am trying to keep new bookmarks from being added. 

Also searched Google and Yahoo and I have been unable to find any type of over ride information.

---

### Post by iMisspell on 2010-01-17
Humm... so are you looking for something like a "Main Bookmark Machine" and have that machine 'server' bookmarks to all the other machines, and the other machine can not add any new bookmarks ? 
The other machines can not save any bookmarks period ?

What kind of environment are you working in ?
The following just popped into my head.

Firefox will save its "browser session bookmarks" when firefox closes, thats how the current version work.

So would something like this work...
Have a script monitor the "Main Machine" firefox folder for the bookmark save, when the save happens, have the script make a copy of the bookmarks file (i forget what it is now, its a sqlite file), save that copy to a general shared location.

Make another script which will run on all the other machines, that script will open firefox on the other machines, but before it opens firefox it will copy the shared sqlite book file to there default location.

Not sure how you would in force this.
And the other machines would not be able to dynamically update there bookmarks with out closing and re-opining, and the Main Machine would have to close down before it could save, so theres alot of nay's with this idea :)

Dont know how google Chrome (or Safari or Opera) handls its bookmarks, maybe thats another option ?

Just some ideas. 

_

---

### Post by lisati on 2010-01-17
Would something like [xmarks]("http://www.xmarks.com/") help?

---

### Post by lyall on 2010-01-17
Firefox bookmark file is located in the 
/home/users_name/.mozilla/firefox/09kkuq12.default/bookmarks.html file

you can also export the bookmarks to a file form Firefox.

Then you can copy the to the other PCs.

In windows I backdoor into a PC from the command line to the machine name.
I do not know how to do it in Ubuntu (Linux).
there should be way way to do it in Ubuntu (Linux) without going to each PC.


good luck and have fun learning

---

