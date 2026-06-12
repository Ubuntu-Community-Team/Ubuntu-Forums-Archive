---
title: "Upgrade 9.04 --&gt; 9.10 has botched Rhythmbox"
date: 2009-11-14
forum: General Help
---

### Post by jamesisin on 2009-11-14
This is a complex issue so if you are just joining us you will want to read through the thread before making a suggestion.  This is especially true for the posts which appear beginning at the top of page 4 where I abandon the upgrade to scrub and rebuild the machine.  There has been a great deal suggested and tested.

Thanks.







Prior to the upgrade process I was attached to a network share (TheCollection) where some 18K flac files are stored (using Samba).  I was able to point Rhythmbox at that share and load all (or nearly all) of the files into the library.  I was then able to play the music in any manner so prescribed under the usual music listening through a music library schema, namely I could push play and expect to listen to several consecutive songs played all the way through and not have to interact with the computer.

Since the upgrade process, I was forced to rebuild the Samba connection (essentially just re-create the bookmark).  This caused me to have to re-establish the library.  Neither of these were much of an issue.  The bookmark was simple and pointing Rhythmbox at the new location was also simple (then I had to wait hours while Rb pulled in all the file information, but ah well).

That being said here is where the troubles arise.

When I direct Rb to play some music it jumps from song to song, track to track, maybe playing half a second of each track until it settles on a track that it wants to play further.  It may or may not finish that track, but when it moves to the next track the same situation arises (bouncing hither and yon).  Any track that it refuses to play will remain refused if I manually seek it out and attempt to play it directly (by double-clicking the track, say).

However, I am able to dump any portion of this collection into Movie Player (then wait a long time for it to catch up) and it will play any and all tracks without issues.  Clearly Rb doesn't like something that's going on here.

Anybody?

---

### Post by jamesisin on 2009-11-15
Also, I have tried re-installing Rb.

Any clues?

---

### Post by arnab_das on 2009-11-15
```
sudo apt-get purge rhythmbox

sudo apt-get autoremove

sudo apt-get install rhythmbox
```

type these in the terminal.

see if it works.

---

### Post by jamesisin on 2009-11-15
Well, that seems to have done the trick.  Thanks for your assistance.

On a peripheral note, I have been seeing this other issue that you may know an answer to.  The share to which Rb attaches is read-only (and will remain so).  Occasionally I mis-remember what I'm doing and attempt to change a tag at that station.  No big thing really; it fails.  However, sometimes when I start Rb I get a string of error dialogs informing me that Rb was unable to save a file (which I surmise relates to this tagging mistake).  Any ideas how to make it shut the #^(& up?

---

### Post by jamesisin on 2009-11-15
A temporary and pitiless illusion...

This did NOT fix the problem.  It may have lessened it, but Rb is still bouncing between tracks as it chooses.

---

### Post by jamesisin on 2009-11-15
A little more information...

Large files seem to be more effected by this.  My collection is largely FLAC files (say 98%).  Smaller files (such as mp3 or wma) last longer (and may even get through most or all of the song) before jumping off to the next track.

These files do not have any trouble in playback through Movie Player.

---

### Post by jamesisin on 2009-11-15
I have built another machine with 9.10 (from scratch).  It is having the same problems with Rhythmbox.

Is there a way to force an older version of Rb on a machine, to downgrade?

---

### Post by arnab_das on 2009-11-16
add jaunty repos to ubuntu karmic and refresh the update.

---

### Post by jamesisin on 2009-11-16
Add the Jaunty repos for Rb?  Not sure how exactly.

---

### Post by jamesisin on 2009-11-24
I have tested Rhythmbox across a DAAP share.  The recipient 9.10 machine experiences the same issue while playing from a DAAP share.

This machine is currently useless since it is supposed to be acting as the media conduit for my living room audio system.  Can someone please help me get this figured out?

---

### Post by jamesisin on 2009-11-30
Anybody?

---

### Post by desperado665 on 2009-11-30
to fix the same issue using amarok, the following always works for me:

```
sudo apt-get install libxine1-ffmpeg
```

I'm afraid that as long as your files are read only, anytime you make a tag update, you will encounter that problem. Look at it as a reminder.... lol.

---

### Post by jamesisin on 2009-11-30
desperado665 - Thanks.  All three of these systems already have that package installed.

---

### Post by 3rdalbum on 2009-11-30
1. Have you tried actually removing the Rhythmbox preferences, which are located at ~/.gnome2/rhythmbox?

2. Maybe check your playback buffer settings; try setting it longer.

3. How exactly did you get Rhythmbox to play music from a network share? It always complained that it couldn't find smb://192.168.0.12, which is why I had to switch to DAAP.

---

### Post by jamesisin on 2009-11-30
1. To which 'preferences' do you refer?  In 9.10 there is no longer a .gnome2/rhythmbox folder.  There is a .local/share/rhythmbox folder but it merely contains the db and playlist xml files (which have been removed periodically during my testing of possible solutions) and a file called audioscrubber.queue (no clue what that one does).

2. I have tried various network buffer settings from the smallest to the largest with no effect.

3. I have tested both a DAAP share and a Samba share.  They both behave the same way.  (I did not have any trouble using either of these methods before moving to 9.10 on this machine.)

---

### Post by jamesisin on 2009-11-30
I got a bit more surgical.  First I ran these:

```
sudo apt-get purge rhythmbox
sudo apt-get autoremove
```

Then I opened Nautilus (gksudo) visited / and ran a search for 'rhythmbox'.  I deleted all of the results.

Then I rebooted the system and installed Rhythmbox afresh.

No change; same old BS.

---

### Post by Megafag on 2009-11-30
> **jamesisin said:**
> No change; same old BS.

Time to install Amarok perhaps?

---

### Post by StuartN on 2009-11-30
> **jamesisin said:**
> No change; same old BS.

I have no idea if it will help, but you could enable buffering by switching on cross-fading in the Rhthymbox preferences.

For what it's worth, I have Rhythmbox playing a DAAP source in versions from 8.04 to 9.10.

---

### Post by Green_Mac on 2009-11-30
No idea if this is related, but I've just posted a query about a problem with RB on a machine which has recently had a fresh install of 9.10.  At first I thought it was great, as I hadn't been able to get RB to write to my NAS drive on my old (Hardy Heron) machine, and now I can - or so I thought.  After successfully dragging and dropping files from a CD to the Music library earlier, it is now flatly refusing to do so with any other disc, saying it can't because the destination "is not a directory".

If this is unrelated, but anyone thinks they might have an answer, please post it under my original query, as I don't want to muddy the waters here.

---

### Post by jamesisin on 2009-11-30
> **StuartN said:**
> I have no idea if it will help, but you could enable buffering by switching on cross-fading in the Rhthymbox preferences.

For what it's worth, I have Rhythmbox playing a DAAP source in versions from 8.04 to 9.10.

I have tried all sorts of configurations including and excluding buffering and cross-fading.  No impact.

Are you sharing FLAC files across the DAAP?

Also, let me restate: no other audio application is having any troubles across the Samba share and my 8.10 machine running Rhythmbox across DAAP or Samba (from the same serving machine) works fine.

---

### Post by jamesisin on 2009-11-30
> **Megafag said:**
> Time to install Amarok perhaps?

I tried using Amarok once, but had trouble getting it to point at the share for its library.  You can PM me if you want to talk about Amarok (I'd like to keep this thread about fixing Rb).

---

### Post by Spectre5 on 2009-11-30
Have you tried running Rhythmbox from the terminal to look for error messages?  There is also a debug mode (using --debug) which will spit out basically EVERYTHING that Rhythmbox does...if you have a lot of files, it will take it a LONG time to start rhythmbox with --debug since it will output loading every single file on the terminal.  Then when playing the file, it will output a lot more information...perhaps when it switches songs on its own there will be an error message or something posted that might help...

```
rhythmbox --debug
```

---

### Post by jamesisin on 2009-11-30
Here is the terminal output (truncated for reasons which will become obvious) for running Rb from the terminal:

```
$ rhythmbox

** (rhythmbox:5023): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:5023): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

(rhythmbox:5023): Rhythmbox-CRITICAL **: rb_rating_render_stars: assertion `pixbufs != NULL' failed
```

That last bit about render stars must scroll past hundreds of times.  I didn't take a close count.

Here is the output from running the debug mode:

```
(rhythmbox:5125): Gtk-CRITICAL **: gtk_tree_row_reference_get_path: assertion `reference != NULL' failed

(rhythmbox:5125): Gtk-CRITICAL **: gtk_tree_row_reference_get_path: assertion `reference != NULL' failed

(rhythmbox:5125): Gtk-CRITICAL **: gtk_tree_row_reference_get_path: assertion `reference != NULL' failed
(16:35:08) [0x9f31028] [rb_shell_player_cmd_play] rb-shell-player.c:2256: play!
(16:35:08) [0x9f31028] [rb_shell_player_playpause] rb-shell-player.c:2285: doing playpause
(16:35:08) [0x9f31028] [rb_shell_player_playpause] rb-shell-player.c:2354: getting entry from play order
(16:35:08) [0x9f31028] [rb_random_play_order_get_next] rb-play-order-random.c:343: choosing enqueued entry
(16:35:08) [0x9f31028] [rb_shell_player_sync_with_source] rb-shell-player.c:2897: playing source: 0xa10c150, active entry: (nil)
(16:35:08) [0x9f31028] [get_times_and_stream] rb-player-gst-xfade.c:2601: not playing
(16:35:08) [0x9f31028] [rb_shell_set_window_title] rb-shell.c:1988: clearing title
(16:35:08) [0x9f31028] [show_controls] rb-visualizer-plugin.c:866: showing controls
(16:35:08) [0x9f31028] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3332: Did not get playing entry : return -1 as length
(16:35:08) [0x9f31028] [rb_shell_player_sync_buttons] rb-shell-player.c:2992: syncing with source 0xa10c150

(rhythmbox:5125): Gtk-CRITICAL **: gtk_tree_row_reference_get_path: assertion `reference != NULL' failed

(rhythmbox:5125): Gtk-CRITICAL **: gtk_tree_row_reference_get_path: assertion `reference != NULL' failed
(16:35:08) [0x9f31028] [paned_size_allocate_cb] rb-shell.c:2663: paned position 496
(16:35:08) [0x9f31028] [paned_size_allocate_cb] rb-shell.c:2664: right_paned position 400

(rhythmbox:5125): Gtk-CRITICAL **: gtk_tree_row_reference_get_path: assertion `reference != NULL' failed

(rhythmbox:5125): Gtk-CRITICAL **: gtk_tree_row_reference_get_path: assertion `reference != NULL' failed
```

Again, you can see which lines repeat ad nausium and were cut from my report here.  I didn't try to get to the top because the output here was vastly larger than without the --debug option.  (The collection consists of more than 20K files.)

Does this tell us anything?

---

### Post by jamesisin on 2009-11-30
Oh, and running from the terminal acted pretty much the same while I was not able to get playback to succeed while in debug.

---

### Post by Spectre5 on 2009-12-01
Try doing this (for each user on the computer):
```
rm -rf ~/.gconf/system/gstreamer
rm -rf ~/.gstreamer-0.10
```

If it still doesn't work, then try running:
```
gstreamer-properties
```
And then select ALSA for the "Default Output" on the "Audio" tab.

---

### Post by jamesisin on 2009-12-01
Can you give me a little more information on your strategy here?  I mean, no other audio program has any difficulty playing across the Samba share on this 9.10 machine.  What is it you are asking me to change exactly?

---

### Post by Spectre5 on 2009-12-01
> **jamesisin said:**
> Can you give me a little more information on your strategy here?  I mean, no other audio program has any difficulty playing across the Samba share on this 9.10 machine.  What is it you are asking me to change exactly?

The first part is removing the gstreamer settings, I've seen in the past that it has has sometimes worked for similar problems.  Any settings here should be re-created as needed.  If you are worried about deleting them, you can just back up those folders first or just rename them temporarily.

The second thing I suggested would be setting the default output to use ALSA as your computer is probably using pulseaudio by default (I think pulseaudio is the default now...which I've seen be the culprit for audio problems in the past).  This could be easily un-done by running the command again and changing it back to autodetect (which is what it should be at now) - so if you would rather, you can test this first since it doesn't remove any files.

---

### Post by jamesisin on 2009-12-01
Thanks for that; understanding is important to me.

I removed the folders you recommended (~/.gconf/system/gstreamer did not exist until I followed your second directive).  This changed nothing.

I then switched to ALSA using gstreamer-properties.  This also did nothing.  So I tried OSS and Pulse as well.  Nada.  Back to AutoDetect.  Same old BS.

I tried a variety of combinations and orders of doing things just in case.

Anything else to suggest?

---

### Post by Spectre5 on 2009-12-01
Hm...looking at the man page gave me another idea...try this to see if we get different output:
```
rhythmbox -D daap
```

You could also try the play-uri option for the client as shown here:
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/178681](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/178681)

The first one would output debug information, but just general stuff and stuff related specifically to DAAP so perhaps that will give us something related to DAAP that we didn't see before.  The second one will try to play a specific file via DAAP so perhaps it will tell us something about a bad connection.

My guess is that there is some package you need that, for some reason, was not included as a dependency...but I'm not sure.  If you don't get any other responses and my suggestion above doesn't provide anything useful, then I'd suggest opening a bug report...

---

### Post by jamesisin on 2009-12-01
Thanks.  I am afraid this was not very fruitful either.

The -D daap option shows me each time a new file is accessed so I get to see it hop from track to track in two places (Rb and the terminal).  No error reported.  (This output is consistent with what I am seeing in my 8.10 functional Rb.)  Those output entries are paired as follows:

```
(18:42:00) [0x85c6408] [rb_daap_src_open] rb-daap-src.c:459: Connecting to DAAP source: daap://[IP.adrs.my.srvr]:3689/databases/1/items/10859.flac?session-id=788042980
(18:42:01) [0xae711598] [rb_daap_src_open] rb-daap-src.c:459: Connecting to DAAP source: daap://[IP.adrs.my.srvr]:3689/databases/1/items/10859.flac?session-id=788042980
```

My functional 8.10 Rb posted these output pairs at the beginning of each track access so I don't imagine this tells us anything.

I couldn't get the trick in the bug report you suggested to provide any meaningful output (except the error as reported in the bug report).

---

### Post by jamesisin on 2009-12-02
Well, I've thrown in the towel and scrubbed the f#(#3%.  I have reinstalled 9.10 and run all the updates.  Testing Rb is fine.  I will keep going one step at a time, and if one of the usual setup or configuration steps breaks it I'll post back.  Otherwise I'll mark this thread as solved (though this is not a solution, per se).

---

### Post by StuartN on 2009-12-02
> **jamesisin said:**
> Otherwise I'll mark this thread as solved (though this is not a solution, per se).

Except that you appear to have identified another situation in which upgrades fail as against new installations.

---

### Post by Spectre5 on 2009-12-02
> **jamesisin said:**
> Well, I've thrown in the towel and scrubbed the f#(#3%.  I have reinstalled 9.10 and run all the updates.  Testing Rb is fine.  I will keep going one step at a time, and if one of the usual setup or configuration steps breaks it I'll post back.  Otherwise I'll mark this thread as solved (though this is not a solution, per se).

Do return to let us know what happens....if some specific package or update is when it breaks...(and I'm sure the devs would like to know about that too!).

---

### Post by jamesisin on 2009-12-02
Ok.  Here is what information I have thus far...

I rebuilt the machine from scratch.  Once I had finished installation I ran all the available updates (what is it now? 143?).  I then added gnome-do (because it drives me nuts not to use it now) and tested Rhythmbox across DAAP to the server (running shared DAAP through Rb).  No problems.

I then stepped through this how to:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

After each step I tested Rb across DAAP.  No problems at any stage.

Then I turned on Compiz and installed the so-called extras.  No problems.

Finally, I loaded the library across the Samba share.  There were import errors (a few) but this seemed within tolerances.  I did this by pointing my library at smb://server/share and instructing Rb to import music using "Music --> Import Folder...".  This took a few hours, maybe (~21K files).

This broke things.  Rb will now occasionally skip from song to song in rapid succession (no rhyme or reason) or it will pause its playback.  This includes moving back to the DAAP share and playing files there.

Through all of this Movie Player (Totem?) has been functioning fine and it can play any file that Rb skips, pauses, or refuses to import.

I am going to attempt to substitute the xml library from my 8.10 machine into the 9.10 machine and see if bypassing the import step has any positive impact.  I have my doubts because even removing the library has not restored the previously flawless performance of Rb.

Thoughts?

---

### Post by ray_h on 2009-12-03
I have a similar problem with RhythmBox when playing from my Samba based library, but not as bad. I typically get it jumping about every 2nd track, and it seems to jump to the next track. I am using Ubuntu 9.10 on my music playing machine and Ubuntu 9.04 on my music server machine. I have also given up on RhythmBox and now only use Movie Player (Totem) to play music. I also have mostly flac files.

---

### Post by Yellow Pasque on 2009-12-03
Have you tried the latest version of rhythmbox (0.12.6)? [https://launchpad.net/~ricotz/+archive/ppa](https://launchpad.net/~ricotz/+archive/ppa)

---

### Post by jamesisin on 2009-12-03
> **ray_h said:**
> I have a similar problem with RhythmBox when playing from my Samba based library, but not as bad. I typically get it jumping about every 2nd track, and it seems to jump to the next track. I am using Ubuntu 9.10 on my music playing machine and Ubuntu 9.04 on my music server machine. I have also given up on RhythmBox and now only use Movie Player (Totem) to play music. I also have mostly flac files.

About how large is your library?

Repeated importing of the library seems to lessen the problem.

---

### Post by Yellow Pasque on 2009-12-03
> **jamesisin said:**
> Is there a repo I can add for that version?  Ubu 9.10 comes with 0.12.5.
Heh, You quoted the link for the repo. [https://launchpad.net/~ricotz/+archive/ppa](https://launchpad.net/~ricotz/+archive/ppa)

---

### Post by jamesisin on 2009-12-03
Damn it.  I tried to delete that before anybody noticed.

---

### Post by Nick L on 2009-12-03
I just installed Ubuntu 9.10 this past weekend - it's my first Ubuntu experience since switching over from XP, and this is the only issue that I'm having.  It seems that with my system that the sound skips over all applications, including Rhythmbox.  The only other program I've used with sound is Firefox, and the same exact thing happening in Rhythmbox happened when I ran a video on YouTube.  Rhythmbox will play a song for a few minutes, but will then speed through the end of the song and proceed to speed through the rest of my library.  Anyone have any ideas (I think our issues are related, but mine is on a smaller scale since I don't run additional programs to playback any media)?

---

### Post by jamesisin on 2009-12-03
Try pointing one of the files Rb has issues with at Movie Player and see if it can play the file without issues.

---

### Post by Nick L on 2009-12-03
Same thing in Movie Player.  Could it be a soundcard issue?  I bought one that wasn't the most expensive just so that I could attach more speakers, but I've never had any issues with it before.

---

### Post by jamesisin on 2009-12-03
Are you using a proprietary driver for your sound card?  Those are sometimes problematic.

Have you gone through this how to:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It looks long but it should only take you about ten minutes to do the stuff relative to your specific version (something like 10 command line inputs maybe).

Then finally, if you are still having sound troubles and you are using PulseAudio (which you probably are) have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

There are only a couple of steps to take on that one, and it should be really easy to test what they ask you to (then post what they ask for if you are still seeing issues).

Reboot after each of these stages.

Hope that gets you back on track.  If you get it narrowed down to just Rb being lame, come on back and see how we are progressing.

---

### Post by Spectre5 on 2009-12-03
Yes, it seems that these are definitely not related.  But jamesisin has given you some good links/advice that should get you on track.

---

### Post by jamesisin on 2009-12-03
A little more information for the spectators...

I compared the xml files from my 8.10 (works perfect) machine and my 9.10 (skips at its pleasure) machine.  I found a file which skipped around 2/3 through and looked at the entry in the files for that track.  No difference in any relevant field (size, duration, &c).

I then found a track which it skipped past (didn't even bother to play a bit of it but the track flashed before Rb moved to another track--I was able to determine the track by using the back arrow).  No difference in any relevant field (size, duration, &c), and going back to it (using the back arrow) it played perfectly.

(My 8.10 machine is showing mount-point as file:///media/Musica which no longer exists, but I can't imagine it is benefiting unfairly from that.  The collection used to reside on this machine at that location before I moved everything over to the 9.10 serving machine.)

Lots of red herrings.  Yum.

---

### Post by Spectre5 on 2009-12-03
Your problem is VERY weird...I don't have the slightest idea what's wrong with it!

---

### Post by jamesisin on 2009-12-03
Yeah, I know.

Oh, and DAAP has not been re-broken by any of this (so I do have a cobbled hobbled work-around for my hi-fi system).

---

### Post by Bob63 on 2009-12-04
jamesisin,

Don't know if this is related either, but I have a similar - but not identical problem. If it seems too off-topic, let me know...I'm not trying to hijack, honest!8-[

I am running a multi-boot system, with 9.04 and 9.10 among the OS's, each in it's own partition. For a while I have been able to run Rhythmbox under 9.04, connect to last.fm, and be able to play "Tag Radio" all night long. However, after installing 9.10, I decided to try Rhythmbox there, to see if the newer version of Rb was worthwhile.

Almost immediately, Rb began having problems, marking various songs in the playlist with the warning bar, repeated attemts to buffer songs, and if it did play, it would only load about 5 songs from the playlist, then load them again in reverse order. Occasionally, it would open a dialog to look for a plugin, but would fail looking for a text/html plugin.

During the course of fiddling with Rb in 9.10, I ***really*** screwed up my whole 9.04, to the point where it was unusable, which required that I re-install (yes, it was that bad). After the install, I copied my home directory from 9.10 to 9.04. Now Rb in 9.04 is acting just like the one in 9.10.

I'm still digging...but I suspect it is something to do with gstreamer, perhaps a missing or corrupt library.

Update: Okay, I searched gstreamer in Synaptic and added[INDENT] gstreamer0.10-plugins-bad-multiverse-dbg (0.10.11-0ubuntu1)
[/INDENT][INDENT] gstreamer0.10-plugins-ugly-multiverse-dbg (0.10.7-2)
[/INDENT]and rebooted, then restarted Rb. [Even though these are the debug versions, it seems to be working] It initially loaded five songs from my last.fm Tag List, then again reloaded the same 5 in reverse order, then the same 5 again in the original order. (??) I used the next track button to step through these, and it is currently loading and playing tracks normally. So, maybe fixed mine, and hope it helps someone else. Keep in mind this is on 9.04. I'll try on 9.10 later and post back.

---

### Post by jamesisin on 2009-12-04
> **Bob63 said:**
> Don't know if this is related either, but I have a similar - but not identical problem.

On the surface they don't appear related, but since I have no idea what is the root of my problem I'm not in a good position to deny it.  Let me know how the debug libraries work out on your 9.10 system.  It would be easy enough for me to test that.

Does anyone else have any comments about this possible solution?

---

### Post by Bob63 on 2009-12-06
jamesisin,

Well, everything seems to be working so far...

Following an earlier post of yours, I completely removed rhythmbox using [I][B]apt-get purge
rhythmbox[/B][/I] then rebooted and re-installed rhythmbox. I also have the debug versions of the libraries installed as I mentioned in my post above. I did this for both 9.04 and 9.10, so now I can listen to the last.fm stream without getting the html/text error in both 9.04 and 9.10.

If this doesn't fix your problem, maybe the issue isn't with rhythmbox itself, but rather with samba. That seems more logical, actually, that samba is having problems reading the music files and manipulating them properly for rhythmbox to get them. You may need to remove/re-install samba and all the pieces, as they may not have upgraded correctly.

You may want to take a look here [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
for help with samba. Even if the tutorial doesn't help, some of the posts in the thread are folks having samba/share/networking issues, and maybe something there will help you out.

Luck!

---

### Post by jamesisin on 2009-12-06
Bob63 - Thanks.  Glad yours is working again.

I'll check out the link you provided.  I have my doubts about it being a Samba issue because no other application is having trouble playing the files in any manner across the Samba share (Movie Player for instance will handle any of the files I dump on it).

(Also, for clarity's sake, I abandoned the upgrade and rebuilt the machine during the course of this thread.  See previous posts for more information.)

---

### Post by mgmiller on 2009-12-06
Just for snorts and giggles, try installing:
```
sudo apt-get install libsdl1.2debian-pulseaudio
```

This will remove the stock package, libsdl1.2debian-alsa.

This change seems to fix weird pulse audio related issues.

If it creates any new issues, just reinstall libsdl1.2debian-alsa, and it will knock out the pulseaudio version.

I only found out about this when installing the openshot video editor from their ppa.  It made this change and I have had no issues of any kind in my 9.10 machines.  I routinely daap share from my 9.10 server to 2 other 9.10 machines in my house without problems.  All my songs are .mp3's though.

---

### Post by Yellow Pasque on 2009-12-06
rhythmbox is a gstreamer app; it doesn't use SDL.

---

### Post by jamesisin on 2009-12-06
mgmiller - Thanks.

Temüjin - Thanks.

---

### Post by jamesisin on 2010-02-18
Just in case anyone is wandering this way, I have since changed my library location designation from 'smb://server/share' to ~/Music wherein I created a soft link to '~/.gvfs/share\ on\ server' and this seems to have put Rb back in control of itself (it's been playing for an hour or so without skipping).

Related post:

[http://ubuntuforums.org/showthread.php?t=1409624](http://ubuntuforums.org/showthread.php?t=1409624)

---

### Post by Spectre5 on 2010-02-20
> **jamesisin said:**
> Just in case anyone is wandering this way, I have since changed my library location designation from 'smb://server/share' to ~/Music wherein I created a soft link to '~/.gvfs/share\ on\ server' and this seems to have put Rb back in control of itself (it's been playing for an hour or so without skipping).

Related post:

[http://ubuntuforums.org/showthread.php?t=1409624](http://ubuntuforums.org/showthread.php?t=1409624)

Wow - you have a lot perseverance, but that's great to hear!  Is it still working?

---

### Post by jamesisin on 2010-02-20
Yep.  Seems to have done the trick.

I really didn't have a lot of option.  I had a workaround in that I could listen on that machine by using a DAAP share from the server (where I would then also have to run Rb).  That worked fine.  But that machine is connected to my hi-fi and there *must* be music at that location.  (The whole point of the server project was to get the CD's out of the living room but still be able to listen to them.)

So I've been listen across the DAAP share and trying things as I saw a possible solution.

---

### Post by Robocoastie on 2010-03-11
Posting my question here because this thread is similar to my issue. I have Ub 9.10 installed on a machine and I've moved all of my music to a shared Music folder there. My other 2 machines run Win7x64. Wa is a laptop, Wb is a desktop, L is the Ubuntu machine.

Before I installed L all my music was on Wb and before iTunes 9 I could see the shared libraries between Wa and Wb in iTunes. iTunes 9 added the "Home Sharing" feature and now Wa and Wb can't see shared music in iTunes much less be able to do the new synch feature.

So, hoping that installing mt-daap and/or running Rhythmbox on the L machine I hoped I could just daap from it to the Win. computers. Alas all I can do is add the L folder as a network drive and build a library with it on the Win machines.

What I have done to try to solve this: the win7 computers are running Windows Firewall. Per the troubleshooting tips at Apple's website I have opened ports 3689(tcp) and 5353(udp) and ensured that "iTunes" and "iTunesHelper" are allowed through.

There doesn't appear to be anything in my router blocking the communication. The sad fact is I likely don't have my router set up ideally even.

---

