---
title: "Rename hundreds of .picasa.ini files?"
date: 2010-09-11
forum: General Help
---

### Post by 2CV67 on 2010-09-11
I usually manage to avoid command line...
It looks like the best answer here but I can't get it to work & would appreciate any help.

In my photos folder, I have hundreds of folders, each with Picasa.ini files.

Unfortunately, a lot of these files are actually ".picasa.ini" files & Picasa 3.0 does not recognize them.

All I want to do is rename all those ".picasa.ini" files to "Picasa.ini".

If there was a GUI way to do this, all in one go, then that would be my prefered method.

I couldn't find one, so reluctantly tried Terminal.
After a lot of reading & trying, still no success.

"locate .picasa.ini" finds all the files easily.

I tried many variants around:
"rename -v -n 's/\.picasa\.ini$/Picasa\.ini/' .picasa.ini"
to run a simulation without screwing anything up yet, but at best they only seem to rename one occurence, not all the files.

I suppose the answer is RTFM, but I have spent quite a bit of time there with no success.

Thanks for any tips!

---

### Post by HermanAB on 2010-09-11
Howdy,

Use the 'find' command.  It can do a recursive search and execute a command when true.  Read the man page or google a bit for help.  It is fairly simple.

---

### Post by inameiname on 2010-09-11
I use Renamer. Works great for me. It's a nautilus script with an easy gui that will do all you want just like that, without use of the terminal. Just select all the ".picasa.ini" files and then right click and select 'Renamer' and use the 'substitute' command to change them to "Picasa.ini". Super easy.

Now, if all the files that you want changed are in various folders, it's still easy. Just do a nautilus search for ".picasa.ini" in the top folder and then select all the comes up in the search, and right click and use the script.

[http://gnome-look.org/content/show.php/Renamer?content=87601](http://gnome-look.org/content/show.php/Renamer?content=87601)

---

### Post by 2CV67 on 2010-09-11
Thanks for those suggestions.

I looked at "Find" command:
[http://linux.die.net/man/1/find](http://linux.die.net/man/1/find)
[http://content.hccfl.edu/pollock/unix/findcmd.htm](http://content.hccfl.edu/pollock/unix/findcmd.htm)
& lots of others.
That reminded me why I HATE command line!
Sorry if that looks like shouting.
It really should be in red, bold, underlined capitals, to look like screaming & tearing hair out...

I was much more encouraged to see there was a GUI method.
So I looked at "Renamer" but it was not in SynApt & at that point I discovered 2 others, hopefully similar.

I installed pyRenamer but it didn't seem to show hidden files & as I need to rename .picasa.ini...

Then I tried GPRename.
That easily & clearly renamed any one file in a folder, but I couldn't see how to get it to handle my problem - hundreds of files, each in a different folder.

After a lot more searching, I gave in & used GPRename - stepping through the folders & switching names in each one.
It's all done now & was simple & clear, but not exactly efficient!

So - I no longer need solutions for this problem, but I would still be interested to hear better answers, maybe for next time!

What command would have done the job?
Something like:
$ find -name .picasa.ini -exec rename 's/\.picasa\.ini/Picasa\.ini/'

...or what?

And how could it be run in 'simulation' mode first?

Thanks again!

---

### Post by inameiname on 2010-09-11
Yeah, Renamer isn't a package in Synaptic. It's merely a Nautilus Script, which can be found in that link I gave. Personally, I think it's much simpler method beats Gprename, PyRenamer, and all the others hands down.

Regardless, glad you got it worked out.

---

### Post by jamesisin on 2010-09-11
You may benefit from my renaming script:

[http://www.soundunreason.com/InkWell/?p=1415](http://www.soundunreason.com/InkWell/?p=1415)

---

### Post by jamesisin on 2010-09-11
As to a simulation mode, I make a copy of the files/folders in question and work on that.  If I fork it up, I throw it away and make a new copy.

---

