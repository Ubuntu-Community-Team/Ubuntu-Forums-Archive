---
title: "Anyone got myth_trailers_grabber working ?"
date: 2010-03-13
forum: General Help
---

### Post by unkle1 on 2010-03-13
Hi all,

The [wiki concerning Apple Trailers]("http://www.mythtv.org/wiki/Myth_Apple_Trailers") and fetching them via script in mythtv has been taken down and as far as I can see the latest version is 4.2.3 but this seems to have the wrong URL for the main-page at apple.com.

Im using this script: [http://www.mythtv.ukpc.net/mythappletrailer-0.4.2.3.tar.gz](http://www.mythtv.ukpc.net/mythappletrailer-0.4.2.3.tar.gz)

```
Warning: file(http://images.apple.com/trailers/rss/newtrailers.rss): failed to open stream: HTTP request failed! HTTP/1.0 404 Not Found
 in /home/dte/myth_trailers_grabber on line 505

Warning: Invalid argument supplied for foreach() in /home/dte/myth_trailers_grabber on line 510
<mythmenu name="TRAILERS">
</mythmenu>
```Tried changing to this URL "http://trailers.apple.com/trailers/home/rss/newtrailers.rss" and got this:
```
<mythmenu name="TRAILERS">

Fatal error: Call to undefined function curl_init() in /home/dte/myth_trailers_grabber on line 542

```Maybe there is an update to 4.2.3 ? or maybe some of you know how to correct this error.

There is a package for mythbuntu by the name mythbuntu-apple-trailers but this does not seem to work either for me.

Thanks in advance! :)

---

### Post by unkle1 on 2010-03-13
So, describing the problem often helps ;)

For future reference :)

I found out that I was missing some cURL-packages.
I used synaptic to install "curl" and "php5-curl".
I then edited these lines in the myth_trailers_grabber script:
```
                $search_pattern_array[] = 'http:\/\/images.apple.com\/movies\/(.*?)\.mov';
                $search_pattern_array[] = 'http:\/\/movies.apple.com\/movies\/(.*?)\.mov';
        } elseif($fmt == 'reg') {
                $movie_url = $movie_url;
                $search_pattern_array[] = 'http:\/\/images.apple.com\/movies\/(.*?)\.mov';
                $search_pattern_array[] = 'http:\/\/movies.apple.com\/movies\/(.*?)\.mov';
        } elseif($fmt == 'lgr') {
                $movie_url = $movie_url . 'large.html';
                $search_pattern_array[] = 'http:\/\/images.apple.com\/(.*?)\.mov';
                $search_pattern_array[] = 'http:\/\/movies.apple.com\/(.*?)\.mov';
        } elseif($fmt == 'trl1') {
                $movie_url = $movie_url . 'trailer1_large.html';
                $search_pattern_array[] = 'http:\/\/images.apple.com\/movies\/(.*?)\.mov';
                $search_pattern_array[] = 'http:\/\/movies.apple.com\/movies\/(.*?)\.mov';
        } elseif($fmt == 'high') {
                $movie_url = $movie_url . 'high.html';
                $search_pattern_array[] = 'http:\/\/images.apple.com\/movies\/(.*?)\.mov';
                $search_pattern_array[] = 'http:\/\/movies.apple.com\/movies\/(.*?)\.mov';
```...to read "trailers.apple.com" instead of "movies/images.apple.com" (the trailing /movies seems ok when browsing the site so I kept that).
                ```
$search_pattern_array[] =  'http:\/\/images.apple.com\/movies\/(.*?)\.mov';
                $search_pattern_array[] =  'http:\/\/movies.apple.com\/movies\/(.*?)\.mov';
Becomes:
                $search_pattern_array[] =  'http:\/\/trailers.apple.com\/movies\/(.*?)\.mov';
                $search_pattern_array[] =  'http:\/\/trailers.apple.com\/movies\/(.*?)\.mov';
And so on...
```Now the script started generating the xml-menu and downloading the .mov-files :D
Unfortunately it ran out of memory about 8 trailers into the script. Editing the memory-settings in php.ini prooved useful but it took 128MB to get through (the default is 32MB).

Now it runs all the way and generates a proper xml-menu for the trailers. Though I still get some errors at some of the last trailers:
From my generated appletrailers.xml:
```
        <button>
                <type>TV_DELETE</type>
                <text>ERROR: Touching Home</text>
                <action>EXEC xmessage -center -timeout 10 There was an error accessing this Apple trailer...</action>
        </button>
```I will try to see if I can figure this out too. (Could be dead links I suppose...)
All hints/advice are welcome ;)

UPDATE: Its not because of dead links, that's for sure. It seems the site is being modified with new layout on some of the trailer-pages so that might the cause. It occured to me that this script possibly violates Apples TOS but maybe there is an "open" alternative ? (like the tmdb-project).

---

### Post by Flaming_Amarant on 2010-03-19
Very interesting topic unkle1... you are not alone ;)

I'm not trying to download them like you, but to watch them in streaming. But I agree they are into something. I'm not sure is anyone else has had success in streaming the trailers.

I get my appletrailers.xml file filled correctly with some videos:

[I]<mythmenu name="TRAILERS">
 <button>
  <type>VIDEO_BROWSER</type>
  <text>Kick-***</text>
  <action>EXEC /usr/bin/mplayer -fs -zoom -really-quiet -user-agent NSPlayer -cache 16000 [http://trailers.apple.com/movies/lionsgate/kickass/ki](http://trailers.apple.com/movies/lionsgate/kickass/ki)
ckass-tlr1a_480p.mov</action>
 </button>[/I]

but it fails on others:

[I]<button>
  <type>TV_DELETE</type>
  <text>ERROR: The Greatest</text>
  <action>EXEC xmessage -center -timeout 10 There was an error accessing this Apple trailer...</action>
 </button>
[/I]
By looking at mplayer (in verbose mode) I got this somewhere:

[I]--- HTTP DEBUG HEADER --- START ---
protocol:           [HTTP/1.0]
http minor version: [0]
uri:                [(null)]
method:             [(null)]
status code:        [302]
reason phrase:      [Moved Temporarily]
body size:          [0]
Fields:
 0 - Server: AkamaiGHost
 1 - Content-Length: 0
 2 - Location: [http://trailers.apple.com/](http://trailers.apple.com/)
 3 - Date: Fri, 19 Mar 2010 19:15:16 GMT
 4 - Connection: close[/I]

A 302 Moved Temporarily?

---

### Post by unkle1 on 2010-03-21
Hello Flaming,

Im glad you find it interesting, I was starting to get afraid the script was a "no no" when it comes to discussing it (because of the restrictions).

Anyway, it seems a good idea to stream it.
Ill be happy to try it, although im almost no good at perl at all.

I found that some of the trailers worked when i chose 720 instead of 480 in the script, but the weird part is it all works when surfing their webpage. Dont know if we are actually experiencing the same phenomenon (with the '302'-status). Maybe their servers detect "crawlers" and replys with this '302' periodically to prevent it ? those "timeouts" in the generated xml is (for my part) always at the end of the script, as if their servers only allow access to a certain number of trailers within a session and then issues the '302' (just a wild and not very qualified guess) ;)
Unfortunately changing $DEBUG from false to true in the script didnt do much for me (have you found a way to make it more verbose ?)

---

