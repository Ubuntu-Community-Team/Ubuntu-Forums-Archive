---
title: "Complete removal of Spotify (purge unsuccessful)"
date: 2012-04-20
forum: General Help
---

### Post by xedi on 2012-04-20
The Spotify client is giving me massive problems regarding offline play in Ubuntu 11.10. Offline play worked fine at first, then I was unable to add any new songs, and now I get an error message saying that offline access for this computer/device has been withdrawn on many occasions. 

Since it worked in the beginning and because I just installed Spotify on my second computer (Ubuntu 12.04) to see whether I have the same problems there and I do not, I decided to remove Spotify completely and reinstall it.

The problem is that I cannot. I tried synaptic and apt-get purge. It will remove the package but there is spotify data because when I install spotify again, it knows my automatic login and other settings, so obviously there is always spotify data left.

So my question is: Is there some more reliable method than synaptic or purge to remove spotify? If not, do you know where Spotify stores its data? I tried searching in the home folder and doing a search for spotify, but nothing comes up after I used purge.

Thanks in advance for your responses.

---

### Post by agillator on 2012-04-20
I know nothing about spotify specifically, but there are some general approaches that can be used. First, the safest methods. Most programs keep their configuration files somewhere in /etc or one of its subdirectories (normally named after the program itself). Check that out. If not there, many store configuration data in some folder in the user's home folder, often in a hidden folder. Check that out. Also, be aware there may configuration data in both places. Also check the documentation for the program - if you haven't found anything in its home page, try just googling for 'spotify configuration' or some such. Also see it its man page (man spotify) tells you anything (if it exists, of course). There is a section near the end of the man page that lists files and it may be there, or it may be elsewhere. If none of this helps, let us know and we'll take the next step.

---

### Post by xedi on 2012-04-20
Thanks for your help. There is no man and I also did not find anything on their homepage.

However, I found [this]("http://benjaminkerensa.com/2012/02/15/spotify-bash-script-for-improved-stability") script, which removes $HOME/.config/spotify and $HOME/.cache/spotify.

So I deleted now the folder in .cache and everything works now! :guitar:

I did not know that there are configurations files in .etc, I did know about home, though. However, I could not find the spotify folders, since as you see it was in the .cache folder.

I did also a search with the "search for files" program before which comes up in the dash, but it never showed me those files, only other spotify related files and folders, which I find weird.

I also assumed that purge would completely remove everything, I wonder why it did not delete every folder in this case.

---

