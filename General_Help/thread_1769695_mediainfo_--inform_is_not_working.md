---
title: "mediainfo --inform is not working"
date: 2011-05-28
forum: General Help
---

### Post by Icche Ghuri on 2011-05-28
I've installed mediainfo CLI downloaded from [here]("http://mediainfo.sourceforge.net/en/Download/Ubuntu"). There is a command
```
mediainfo --help-inform
```

You will find the usage of --inform paramete. But it doesn't work for me. Like the command above will show you an example like this,

```
MediaInfo --Inform=Video;%AspectRatio% FileName
```

I tried with this,
```
mediainfo --Inform=Video;%AspectRatio% /media/Alpha/Movies/Up.mp4
```

but it gives me this error,
```
Usage: "MediaInfo [-Options...] FileName1 [Filename2...]"
"MediaInfo --Help" for displaying more information
bash: fg: %AspectRatio%: no such job

```
Any idea what's wrong?

---

### Post by rduke15 on 2012-09-25
You need to use quotes around your Inform parameter, because Bash uses ";" as a command separator. So what you are actually sending to Bash is 2 commands:

    mediainfo --Inform=Video
and
    %AspectRatio% /media/Alpha/Movies/Up.mp4interprets

and of course you just get 2 errors back.

What you want is:

```
mediainfo --Inform="Video;%AspectRatio%" /media/Alpha/Movies/Up.mp4
```

---

