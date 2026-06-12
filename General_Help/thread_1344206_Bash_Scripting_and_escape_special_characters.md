---
title: "Bash Scripting and escape special characters"
date: 2009-12-02
forum: General Help
---

### Post by asensio on 2009-12-02
First of all, I don't know what I'm doing so be patient :D

I'm using a simple script to "tweet" the song I'm listening to in Audacious:

```
#!/bin/bash
#
USERNAME=my_username;
PASSWORD=my_password;
tpost="&#9835; $(audtool2 current-song)";
echo ${#tpost}
curl -u $USERNAME:$PASSWORD -d status="$tpost" http://twitter.com/statuses/update.xml
```

Well, here's the problem: If audtool2 command outputs something like "Bacon & Eggs", the script will only post "Bacon " because of the "&" character. So, how can I escape special characters in the *tpost* variable?
Thanks in advance.
Cheers
Asensio

---

### Post by StuartN on 2009-12-02
> **asensio said:**
> Well, here's the problem: If audtool2 command outputs something like "Bacon & Eggs", the script will only post "Bacon " because of the "&" character.

The backslash works for most characters, including the space, e.g. Bacon\ \&\ Eggs, although some form of quotes around the track name would also work and take less effort.

---

### Post by asensio on 2009-12-02
The backlash doesn't work in this case because the special character can be anywhere in the variable. I have, as you say, to escape the entire track name. But how?
:-k

---

### Post by StuartN on 2009-12-02
> **asensio said:**
> The backlash doesn't work in this case because the special character can be anywhere in the variable. I have, as you say, to escape the entire track name. But how?
:-k

The following will set tpost to the output of audtool2, surrounded by single quotes.

```
tpost=\'&#9835; $(audtool2 current-song)\'
```

---

### Post by asensio on 2009-12-02
I tried tpost=\'&#9835; $(audtool2 current-song)\' and CLI output was:
> 
/home/asensio/.twittersongpost: line 5: Tattered: command not found
0
<?xml version="1.0" encoding="UTF-8"?>
<hash>
  <request>/statuses/update.xml</request>
  <error>Client must provide a 'status' parameter with a value.</error>
</hash>

I tried tpost="\'&#9835; $(audtool2 current-song)\'" and it posted > \'&#9835; Tattered on twitter for a track named "Tattered & Torn"

---

### Post by StuartN on 2009-12-03
> **asensio said:**
> I tried tpost=\'&#9835; $(audtool2 current-song)\' and CLI output was:

I think you need to assign either tpost="\"&#9835; $(audtool2 current-song)\"". An echo of the curl command gives me curl -u my_username:my_password -d status="&#9835; My song & noise" [http://twitter.com/statuses/update.xml](http://twitter.com/statuses/update.xml)

I am using tpost=$(rhythmbox-client --print-playing), with a trackname with an ampersand. It is correctly assigned, although the outer quotes are not necessary in the terminal and ARE necessary in a script.

This is a really nice idea, thanks. I have been doing something related using Mutt to post my system health status by email [http://ubuntuforums.org/showthread.php?t=1284459](http://ubuntuforums.org/showthread.php?t=1284459) but Twitter would be a neat remote system log too. How would you read Twitter messages and automatically reply?!

---

### Post by asensio on 2009-12-03
Thanks StuartN, I tried all of your suggestions but no success.

> How would you read Twitter messages and automatically reply?!
About reading Twitter messages, I can only tell you to use a Twitter Client like Gwibber. As "automatically reply" you mean automatically post another tweet? Well in my case is simple because I use a plugin in Audacious that runs a command at song change. See if [_any of this_]("http://www.ibm.com/developerworks/linux/library/l-friendfeed/index.html") can help you. Sorry.

---

### Post by pbrane on 2009-12-03
instead of using
```

curl -u $USERNAME:$PASSWORD -d status="$tpost" http://twitter.com/statuses/update.xml

```

try
```

curl -u $USERNAME:$PASSWORD **--data-urlencode** status="$tpost" http://twitter.com/statuses/update.xml

```

the amperstand is probably being interpreted in the POST instead of being passed thru.
you may need to use **--data-binary** instead though, no processing of the string that way.

man curl may help as well.

---

### Post by asensio on 2009-12-03
Thank you very much pbrane, the --data-urlencode did the trick.
:guitar:

---

### Post by asensio on 2010-02-03
Well, I used this script until my twitter was clotted with > #nowplaying &#9835; Song (Album) - Artist

I want to try something a little different: Post, just once, the Album and Artist, like this: #nowplaying &#9835; Album - Artist

I know that the command ```
audtool2 current-song-tuple-data album
``` and ```
audtool2 current-song-tuple-data artist
``` will get me the Album and the Artist. 

But here things get complicated. I need a script that recognizes that audacious2 is, not on, but playing a song, and then post it to twitter.

Like this: Audacious ON --> Audacious Play --> Start Script --> Post in Twitter 

Any advise?
Thank you

---

### Post by asensio on 2010-02-04
No ideas? Anyone?

---

### Post by ushills on 2010-02-04
```
echo -E ${#tpost}
```

From the echo man page

-E  Disable the interpretation of the following backslash-escaped characters

---

### Post by asensio on 2010-02-04
Thanks ushills but that problem was fixed...
I have a new one:

> Well, I used this script until my twitter was clotted with
Quote:
#nowplaying &#9835; Song (Album) - Artist
I want to try something a little different: Post, just once, the Album and Artist, like this: #nowplaying &#9835; Album - Artist

I know that the command
Code: audtool2 current-song-tuple-data album

and

Code: audtool2 current-song-tuple-data artist

will get me the Album and the Artist.

But here things get complicated. I need a script that recognizes that audacious2 is, not on, but playing a song, and then post it to twitter.

Like this: Audacious ON --> Audacious Play --> Start Script --> Post in Twitter

Any advise?
Thank you

---

### Post by StuartN on 2010-02-05
> **asensio said:**
> Thanks ushills but that problem was fixed...
I have a new one:

**audtool --playback-playing** should return the string "OK" if Audacious is currently playing. I assume audtool2 has a similar option.

```
if [ $(audtool --playback-playing) == "OK ] ; then
  # send your tweet
fi
```

---

### Post by asensio on 2010-02-05
Thank you StuartN, but your code gives me an error

"[: ==: unary operator expected"

I made several modifications like:

```
if [ [COLOR="Red"]"[/COLOR]$(audtool2 --playback-playing)[COLOR="Red"]"[/COLOR] [COLOR="Red"]![/COLOR]= "OK" ] ; then
  # send your tweet
fi 
```

But I keep getting Audacious always "on" even when it is off 

Since I'm here ;) another question:

I need the script to "know" the playlist path, where de album art is (the string result is something like /path/to/artist - abum). How can I get that path? Using autool2? But how?

(I post this in Audacious Forum but it is kind of idle)

---

### Post by StuartN on 2010-02-08
> **asensio said:**
> Thank you StuartN, but your code gives me an error

According to [http://linux.die.net/man/1/audtool](http://linux.die.net/man/1/audtool), **audtool2 --playback-playing** should return "OK" if playing. Perhaps **man audtool2** would give you more recent options. Try using a single "=":
```
if [ "$(audtool2 --playback-playing)" = "OK" ] ; then
  echo "Playing now"
fi 
```

According to the same manual, **audtool2 --playlist-song-filename 1** should return the filename of the first song in the playlist, so **audtool2 --playlist-song-filename $(audtool2 --playlist-position)** should return the filename of the current song.

---

### Post by asensio on 2010-02-08
Thank you StuartN for your reply. I tried:

```
if [ "$(audtool2 --playback-playing)" = "OK" ] ; then
  echo "$(audtool2 --playlist-song-filename $(audtool2 --playlist-position))" ; else
  echo "Not Playing"
fi
```

I keep getting "Not Playing"...

Trying just the **echo "$(audtool2 --playlist-song-filename $(audtool2 --playlist-position))"** bit, the return is a string where spaces are interpreted as "%20". There must be something to escape this... The echo man page didn't help.

But thank you for your help. I just suck at coding :D
Cheers

---

### Post by asensio on 2010-02-11
No one can help?

---

### Post by falconindy on 2010-02-11
When using Bash, **always** opt for double square brackets over the old crusty single brackets.

[ $somevar = "value" ] is invalid when $somevar is empty, because the expression appears as [  = "value" ] (and throws an error)
[[ $somevar = "value" ]] is valid when $somevar is empty, because Bash is cool like that.

If you're intent on keeping POSIX compliance, you can just reverse the comparison:
[ "value" = $somevar ]  this will always be a valid comparison because you're starting with a static value to compare to something else.

I don't use audacious, but I suspect you may have better results changing to the proper Bash syntax.

---

### Post by StuartN on 2010-02-14
> **asensio said:**
> I keep getting "Not Playing"...

What is the output of **audtool2 --playback-playing** when a song is playing, paused and not playing? The old manual states that it should return "OK" when a song is playing, and the exact output is what should go in the comparison (so "Ok" is distinct from "OK").

> **asensio said:**
> Trying just the **echo "$(audtool2 --playlist-song-filename $(audtool2 --playlist-position))"** bit, the return is a string where spaces are interpreted as "%20". There must be something to escape this...

You could pipe the output through sed to substitute the "%20" representations of the space character with real spaces like this:

```
echo "$(audtool2 --playlist-song-filename $(audtool2 --playlist-position) | sed 's/%20/ /g')
```

---

### Post by asensio on 2010-03-09
I think I'm being ambitious here but I want to try another thing...

I can post to twitter the current song with **audtool2 --current-song** (using the Song Change plugin). The output is: Song (Album - Artist)

Now I was thinking of a script that, at each song change, could compare the output from the previous song. So if I was listening to the same album it would post only _once_ the album and artist , if I was listening to varied albuns or artists it would post the song, artist and album.

Any ideas how could this be done?

p.s. - I'm also thinking of posting the album art to twitpic but... one step at a time.

p.s.2 - StuartN 

> What is the output of audtool2 --playback-playing when a song is playing, paused and not playing?

I can't get any output, strange...

---

