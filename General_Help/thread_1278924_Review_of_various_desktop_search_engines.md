---
title: "Review of various desktop search engines"
date: 2009-09-30
forum: General Help
---

### Post by dE_logics on 2009-09-30
These are what I tried and what I think about - 
[B]
pinot - [/B]

Apparently it look extremely good, but peeping more into the software will make you realize that there's no option to 'reindex'...or exactly you have no control over the indexing process.

**strigi - **

I used the QT based interface to use it...and I was surprised to see a desktop search engine consisting of - 
1)list of folders to index
2)A search bar
3)4 sets of buttons
4)a file and edit menu on top

Talk about being compact and simple!...THIS MUCH simplicity makes the thing useless!!

Anyway, it did qualify my minimum requirements; but after using it, I realized that after you index your desired directories and exit the program, the software 'forgets' what folders did it index i.e the folder list is set to default after that and removing even one destroys the index completely.

Further more once the daemon starts...you have no options to stop it (that button(out of 4) does not work).

Worst of all...it has a ABYSMAL requirement of memory, it easily chewed all my 3 GB with ease...thus it's unusable.

**Google search**
FINALLY something usable but extremely slow when indexing...it takes an unusually long time and does everything in the background.

However the major problem with this is it's extremely inaccurate...the term 'Bernoulli' yielded only 21 results while other search engines yielded 50 + (by others I mean the default gnome search and recoll)

More over I could not specify the complete set of directories which I wanted to index...it just doesn't take in deeper levels of subdirectries!...as a result the whole my documents folder was listed.

**Docco -**

This thing is not even close to something called as a "desktop search engine"...it's looks like a professional tools to generate relations off various sets.

**Beagle - **

This software has no opinion at all!...all it does is sit ducks in your system and has pushable buttons...a perfect toy for a kid!

Maybe the beagle is too dam chubby.

**Terrier Search Engine - **

THIS SOFTWARE HAS MPL LICENCE...that's what I learnt realllly about this software...the people maintaining this treat this as if it's a super spy top secret haxxor software which then have been developing for a century...you actually have to fill a form to download this...then log in with a username and password to a website...AND EVEN THEN...the downloaded file is corrupt and varies in size.

**GNOME Storage (in built) and or Meta Tracker**

Are these 2 the same...and are they the same thing as preinstalled in ubuntu?

Anyway, this thing will monopolize on your system...you have absolutely NO CONTROL over it once the service starts...you have to end it forcefully. With me...I could not go further than the 3rd result page cause "the daemon was busy"..and as I said before I have no control over it.

Furthermore it's confusing; it's a single program having 2 dialogs...one search and one preference.

**recoll - **

Finally..something close to perfect, but there's no way to stop the indexing process except closing the whole program.

**kat - **
This cat was the ideal match for me...but unfortunately she couldn't make it through the whole indexing process...it's 'crashed' on something.

Now whatever results I got from the search off all softwares were missing on some files...for e.g a PDF had 'Bernoulli' string in it and none of the search tools pointed to this file...this is very unreliable.

Here are my minimum requirements for a search engine - 
Should have ability to 'reindex'.
I do not require file monitoring, and so I should have control to shut the program down completely without ANY residual processes.
Custom paths for indexing.
Accuracy; which recoll was missing.

That's about it...but none of the software could make it.

Anymore programs?

If anyone could fix kat, it will be very nice...in general if you could give advices on each of the programs tried.

---

### Post by nortexoid on 2010-01-10
Hey, thanks for this.

I have the same problem and opinion about strigi: it's terrible. It never remembers added/removed directories or filters, and it doesn't appear to integrate with anything. The user interface is so sparse there's no way to sort efficiently through the results it returns. I have no idea why it's installed by default with the latest KDE.

Anyway, your post led me to Recoll which I'm testing out. So far so good. A small concern: it looks to be using Qt 3 rather than 4. I notice screenshots on Recoll's website where it looks like a normal KDE4 application. What's up with that? I install via the backports PPA.

---

