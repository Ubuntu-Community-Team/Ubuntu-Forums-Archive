---
title: "Parse error."
date: 2010-10-14
forum: General Help
---

### Post by senakahks on 2010-10-14
Hi,

I am trying to run this script.

```
#!/usr/bin/liquidsoap
# Log dir
set("log.file.path","/tmp/basic-radio.log")

# Music
myplaylist = playlist("~/radio/music.m3u")
# Some jingles
jingles = playlist("~/radio/jingles.m3u")
# If something goes wrong, we'll play this
security = single("~/radio/sounds/default.ogg")

# Start building the feed with music
radio = myplaylist
# Now add some jingles
radio = random(weights = [1, 4],[jingles, radio])
# And finally the security
radio = fallback(track_sensitive = false, [radio, security])

 # Stream it out
output.icecast(%vorbis,
  host = "localhost", port = 8000,
  password = "hackme", mount = "basic-radio.ogg",
  radio)

```But I am getting this error: :(

Line 20, char 17 before "%": Parse error. 

Please help me to fix this problem.

Thanks

---

### Post by zound on 2010-11-12
tryout:

output.icecast.lame(host="localhost",port=8000,password="xx",mount="radio.mp3",mksafe(play))

works for me with 0.9.2-1 on ubuntu 10.04

greetings zound

---

