---
title: "trying to download apple trailers with a 'for i in cat x' script"
date: 2010-12-11
forum: General Help
---

### Post by carn1x on 2010-12-11
Ok, for those unaware Apple trailers do not allow downloading of trailer MOV files unless the correct user-agent is provided. Therefore the following command is required to download using wget:


```
wget -U 'QuickTime/7.6.2' http://trailers.apple.com/movies/dreamworks/realsteel/realsteel-tlr1_h480p.mov

```

In a situation where this works, the following is output:

```
--2010-12-11 22:08:39--  http://trailers.apple.com/movies/dreamworks/realsteel/realsteel-tlr1_h480p.mov
Resolving trailers.apple.com... 219.76.10.192, 219.76.10.144
Connecting to trailers.apple.com|219.76.10.192|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 26473738 (25M) [video/quicktime]
Saving to: `realsteel-tlr1_h480p.mov.2'
```

So I thought I'd try and download a bunch of them using a file that holds a list of trailer URLs, using the following script:

```
for i in `cat 11dec10`;do wget -U \'QuickTime/7.6.2\' $i;done

```

Unfortunately this does not work, and acts as if the incorrect user-agent is provided. The output is instead:

```
--2010-12-11 22:08:21--  http://trailers.apple.com/movies/dreamworks/realsteel/realsteel-tlr1_h480p.mov
Resolving trailers.apple.com... 219.76.10.144, 219.76.10.192
Connecting to trailers.apple.com|219.76.10.144|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://trailers.apple.com/ [following]
--2010-12-11 22:08:21--  http://trailers.apple.com/
Reusing existing connection to trailers.apple.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 25298 (25K) [text/html]
Saving to: `realsteel-tlr1_h480p.mov.1'
```

If I put an echo at the front of the command, it outputs the desired command perfectly. If I then evaluate that command with a copy-paste, the file downloads fine.

I understand this might be a problem specific to Apple and nothing to do with Ubuntu, however this problem is surely solvable in the context of my command-line right?

Thanks for any advice :)

---

### Post by DaithiF on 2010-12-11
why escape the quotes with the leading \ ?  try without escaping them.

---

### Post by carn1x on 2010-12-11
Ahh yes that worked :). I had the list of files also containing yahoo trailers which require quotes as the URL contains '?' so I guess I got lost with my quotes! Thanks :D

---

