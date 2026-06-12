---
title: "lyrics fetching programme,"
date: 2010-02-20
forum: General Help
---

### Post by nos09 on 2010-02-20
Ok here is the thing i m a green day lover. and sometimes i dont understand what billy joe is speaking !!! so i have to have the lyrics..

is there any programme that fetches lyrics for me **_[COLOR="DarkRed"]and[/COLOR]_** saves it somewhere that i can access them later when being offline ??

yes i can do it by rhythembox it fetches them but i have to copy them manually and past 'em in simple text editor.. and it something i dont like to do. and specially being in ubuntu.. you know what i mean...:D

we always finds a way rather then saying that try a different thing.. !!!!

:guitar:

---

### Post by nos09 on 2010-02-20
Ok here is the thing i m a green day lover. and sometimes i dont understand what billy joe is speaking !!! so i have to have the lyrics..

is there any programme that fetches lyrics for me and saves it somewhere that i can access them later when being offline ??

yes i can do it by rhythembox it fetches them but i have to copy them manually and past 'em in simple text editor.. and it something i dont like to do. and specially being in ubuntu.. you know what i mean...

we always finds a way rather then saying that try a different thing.. !!!!

:guitar:

---

### Post by nos09 on 2010-02-20
Ok here is the thing i m a green day lover. and sometimes i dont understand what billy joe is speaking !!! so i have to have the lyrics..

is there any programme that fetches lyrics for me **_[COLOR="DarkRed"]and[/COLOR]_** saves it somewhere that i can access them later when being offline ??

yes i can do it by rhythembox it fetches them but i have to copy them manually and past 'em in simple text editor.. and it something i dont like to do. and specially being in ubuntu.. you know what i mean...:D

we always finds a way rather then saying that try a different thing.. !!!!

:guitar:

---

### Post by GSF1200S on 2010-02-20
> **nos09 said:**
> Ok here is the thing i m a green day lover. and sometimes i dont understand what billy joe is speaking !!! so i have to have the lyrics..

is there any programme that fetches lyrics for me and saves it somewhere that i can access them later when being offline ??

yes i can do it by rhythembox it fetches them but i have to copy them manually and past 'em in simple text editor.. and it something i dont like to do. and specially being in ubuntu.. you know what i mean...

we always finds a way rather then saying that try a different thing.. !!!!

:guitar:

Im not sure, but I think that Amarok saves the lyrics in the tags section of the mp3 file. Of course, if youre using Amarok, it will be displayed in the center column. It does require a TON of KDE libraries though, so you may not like that. You might also check out Banshee media player as well..

---

### Post by nos09 on 2010-02-20
Ok here is the thing i m a green day lover. and sometimes i dont understand what billy joe is speaking !!! so i have to have the lyrics..

is there any programme that fetches lyrics for me **_[COLOR="DarkRed"]and[/COLOR]_** saves it somewhere that i can access them later when being offline ??

yes i can do it by rhythembox it fetches them but i have to copy them manually and past 'em in simple text editor.. and it something i dont like to do. and specially being in ubuntu.. you know what i mean...:D

we always finds a way rather then saying that try a different thing.. !!!!

:guitar:

---

### Post by nos09 on 2010-02-20
ok. but is it possible to access them while being offline. 

what about backup ..???

---

### Post by anonbeat on 2010-02-20
> **nos09 said:**
> Ok here is the thing i m a green day lover. and sometimes i dont understand what billy joe is speaking !!! so i have to have the lyrics..

is there any programme that fetches lyrics for me **_[COLOR="DarkRed"]and[/COLOR]_** saves it somewhere that i can access them later when being offline ??

yes i can do it by rhythembox it fetches them but i have to copy them manually and past 'em in simple text editor.. and it something i dont like to do. and specially being in ubuntu.. you know what i mean...:D

we always finds a way rather then saying that try a different thing.. !!!!

:guitar:

Guayadeque Music Player will do it soon. Right now it saves lyrics into audio files but its planned to save them too to a directory you specify.

see here [http://ubuntuforums.org/showthread.php?t=1380811](http://ubuntuforums.org/showthread.php?t=1380811)

Greets

---

### Post by overdrank on 2010-02-20
Please do not create multiple threads on the same issue. Threads merged

---

### Post by mechro on 2010-02-20
Rythmbox stores lyrics in **.lyrics** (a hidden folder in your home).

I don't know whether this is deleted on log-out or shutdown.

You may find you've got a ton of lyrics in **.lyrics** already

---

### Post by nos09 on 2010-02-20
> **mechro said:**
> Rythmbox stores lyrics in **.lyrics** (a hidden folder in your home).

I don't know whether this is deleted on log-out or shutdown.

You may find you've got a ton of lyrics in **.lyrics** already

and where is it exactly ? i mean the path ?


and i m extremely sorry for multiple threads. i don know how that happend i thought my posts are not actually being posted. i didn't find them in my " find all your threads" section so i thought it could be some mistake or may be server is down.

sorry again.:confused:

---

### Post by mechro on 2010-02-20
The path is **/home/username/.lyrics**

To see it in Nautilus set **View** to **Show Hidden Files**

If Rythmbox automatically looks in this file for lyrics then I would expect all your lyrics will be available "offline".

---

### Post by nos09 on 2010-02-20
> **mechro said:**
> The path is **/home/username/.lyrics**

To see it in Nautilus set **View** to **Show Hidden Files**

If Rythmbox automatically looks in this file for lyrics then I would expect all your lyrics will be available "offline".

thanks .

is there any way to add sites in rhythembox for fetching lyrics. some of lyrics are not found on current setting..?

---

### Post by stinkeye on 2010-02-20
CoverGloobus will display lyrics and guitar tabs for rhythmbox and a number of other players.

Add the repository
```
sudo add-apt-repository ppa:gloobus-dev/covergloobus
```

Update and install
```
sudo apt-get update && sudo apt-get install covergloobus
```

If you click on the small triangle at the top left there is an option to save the file.
You can also find the lyrics in
```
~/.cache/covergloobus/lyrics
```

In the configure > lyrics tab
mark "*Try other engines if nothing found*" box, for better results.

---

### Post by nos09 on 2010-02-21
> **stinkeye said:**
> CoverGloobus will display lyrics and guitar tabs for rhythmbox and a number of other players.

Add the repository
```
sudo add-apt-repository ppa:gloobus-dev/covergloobus
```

Update and install
```
sudo apt-get update && sudo apt-get install covergloobus
```

If you click on the small triangle at the top left there is an option to save the file.
You can also find the lyrics in
```
~/.cache/covergloobus/lyrics
```

In the configure > lyrics tab
mark "*Try other engines if nothing found*" box, for better results.

sorry for asking another question which is not related to this thread. 
but cant help myself from asking which version u are using ?? i mean i looked at the image you atteched and i m really impressed what did you installed your desktop is so..... cool. how can i turn mine into like yours ????

---

### Post by stinkeye on 2010-02-21
> **nos09 said:**
> sorry for asking another question which is not related to this thread. 
but cant help myself from asking which version u are using ?? i mean i looked at the image you atteched and i m really impressed what did you installed your desktop is so..... cool. how can i turn mine into like yours ????
It's karmic using covergloobus for lyrics and album cover and docky as the mac style dock.
Icons are [_**[COLOR="DarkRed"]Gartoon Redux[/COLOR]**_]("http://www.gnome-look.org/content/show.php/Gartoon+Redux?content=74841")
The top part is just gnome-panel using applets and conky underneath.
The play time display under the covergloobus album cover is also conky.
Send me a private message and I'll help you with some of the setup.
You have to customize conky to your particular setup...eg screensize hardware and you may have to add other programs like lm-sensors to display certain stuff.

If you want to use conky, download the conky-all package through
synaptic package manager.

Here's a link to help you get started with conky:
[_**[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]**_]("http://ubuntuforums.org/showpost.php?p=5436679&postcount=1")

---

### Post by nos09 on 2010-02-22
> **stinkeye said:**
> It's karmic using covergloobus for lyrics and album cover and docky as the mac style dock.
Icons are [_**[COLOR="DarkRed"]Gartoon Redux[/COLOR]**_]("http://www.gnome-look.org/content/show.php/Gartoon+Redux?content=74841")
The top part is just gnome-panel using applets and conky underneath.
The play time display under the covergloobus album cover is also conky.
Send me a private message and I'll help you with some of the setup.
You have to customize conky to your particular setup...eg screensize hardware and you may have to add other programs like lm-sensors to display certain stuff.

If you want to use conky, download the conky-all package through
synaptic package manager.

Here's a link to help you get started with conky:
[_**[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]**_]("http://ubuntuforums.org/showpost.php?p=5436679&postcount=1")


i've installed the covergloobus and its working fine but problem is that when the song change the lyric window doesn't show the new lyrics files i have to close it and then reopen it to view new lyrics, and i also tired to configre the covergloobs and checked the option " refresh lyrics tab when song changed " but no effect ? any other way.?

---

### Post by tom.swartz07 on 2010-02-22
> **nos09 said:**
> i've installed the covergloobus and its working fine but problem is that when the song change the lyric window doesn't show the new lyrics files i have to close it and then reopen it to view new lyrics, and i also tired to configre the covergloobs and checked the option " refresh lyrics tab when song changed " but no effect ? any other way.?

Ive noticed that too, i think its simply a bug with the latest release. 
Id say just stick with it for a little while, im sure theyll fix it with a new update soon

---

### Post by nos09 on 2010-02-22
> **tom.swartz07 said:**
> Ive noticed that too, i think its simply a bug with the latest release. 
Id say just stick with it for a little while, im sure theyll fix it with a new update soon

then can i get old versin if its workin fine

---

### Post by stinkeye on 2010-02-22
> **nos09 said:**
> i've installed the covergloobus and its working fine but problem is that when the song change the lyric window doesn't show the new lyrics files i have to close it and then reopen it to view new lyrics, and i also tired to configre the covergloobs and checked the option " refresh lyrics tab when song changed " but no effect ? any other way.?
Behaves the same for me.It's a known bug that's been reported.
If you choose open in separate windows the lyrics refresh.
Close the lyrics window and reopen and they should now refresh.
Separate windows just means a different window for lyrics and tabs.

---

### Post by alindgr1 on 2010-02-22
Songbird does this.  ([http://www.getsongbird.com/](http://www.getsongbird.com/)).  The lyrics fetcher is an add-on that works wonderfully for me.  It saves the lyrics in the metadata of the song, I believe.  I am using it right now, as we speak.  I do have a problem with it not being able to find the lyrics for a very few songs, but in those cases, I usually am able to find them and add them myself.

---

### Post by stinkeye on 2010-02-22
I also use the *place windows* plugin in ccsm > window management
to keep the lyrics window in the same position.

---

### Post by nos09 on 2010-02-22
someone said its a bug in "new" version. can i change back to old one.?

---

### Post by tom.swartz07 on 2010-02-22
> **nos09 said:**
> someone said its a bug in "new" version. can i change back to old one.?

You *can* but its not really recommended. As the new updates are installed, the core program depends on certain versions of other programs to be installed, assuring that everything is how it should be and is up to date. 

In order to get back to an older version, you need to manually track down the list of dependencies and then compile the older version yourself. All of them could be found on the PPA site.

Like I said, I really really wouldnt recommend it, as you will be opening up a humongous can of worms by trying to roll back to previous versions of multiple programs, not just covergloobus. 


Just stick with it, Im sure a new update will be coming within the week. I just checked the Launchpad site, and there is an entire branch dedicated to fixing the lyrics page. Its still in the "experimental" stage, so, again, DONT USE IT unless you really want to help hammer out some bugs. [https://code.launchpad.net/~jaapz-b/covergloobus/lyricsfix](https://code.launchpad.net/~jaapz-b/covergloobus/lyricsfix)

---

### Post by nos09 on 2010-02-22
> **alindgr1 said:**
> Songbird does this.  ([http://www.getsongbird.com/](http://www.getsongbird.com/)).  The lyrics fetcher is an add-on that works wonderfully for me.  It saves the lyrics in the metadata of the song, I believe.  I am using it right now, as we speak.  I do have a problem with it not being able to find the lyrics for a very few songs, but in those cases, I usually am able to find them and add them myself.

good. just the thing i wanted. just tell me where are the lyrics being store ? i mean the path on my hard drive?

---

### Post by nos09 on 2010-02-22
> **alindgr1 said:**
> Songbird does this.  ([http://www.getsongbird.com/](http://www.getsongbird.com/)).  The lyrics fetcher is an add-on that works wonderfully for me.  It saves the lyrics in the metadata of the song, I believe.  I am using it right now, as we speak.  I do have a problem with it not being able to find the lyrics for a very few songs, but in those cases, I usually am able to find them and add them myself.

how do i scan for entire library for lyrics at once. i got 1024 files.
is it possible to batch search for lyrics?

---

### Post by nos09 on 2010-02-22
problem solved.
and where are the lyrics saved?
i mean the path of lyric files?

---

### Post by alindgr1 on 2010-02-27
Songbird stores the lyrics in the metadata of the song files (MP3 tag), so there really is no backup that you can do.  As long as you keep the same song files, the lyrics will be there.

I have reloaded my computer several times since I started using Songbird.  If you have to, just reinstall songbird, then reinstall LyricsMaster.  Open the preferences for it, at the bottom of that window will be a long bar that says "Scan entire library for lyrics."  That will go through your library and look for the songs that already have lyrics in the metadata.

Let me know if you need any more help.

---

### Post by nos09 on 2010-02-28
> **alindgr1 said:**
> Songbird stores the lyrics in the metadata of the song files (MP3 tag), so there really is no backup that you can do.  As long as you keep the same song files, the lyrics will be there.

I have reloaded my computer several times since I started using Songbird.  If you have to, just reinstall songbird, then reinstall LyricsMaster.  Open the preferences for it, at the bottom of that window will be a long bar that says "Scan entire library for lyrics."  That will go through your library and look for the songs that already have lyrics in the metadata.

Let me know if you need any more help.

got it..
thanks.a lot

---

### Post by alindgr1 on 2010-02-28
Welcome, no problem.

---

### Post by nothingspecial on 2013-03-04
Old thread closed

---

