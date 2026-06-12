---
title: "Need help shaping an advanced wget command"
date: 2009-08-01
forum: General Help
---

### Post by alan_daniel on 2009-08-01
Hey, I have a wget command that I want to make to automate the downloading of archived audio podcasts of the NPR show Wait, Wait, Don't Tell Me. They just redesigned their website, and it now uses a conventional approach to archived shows and their mp3 files. And yes, you can download them in individual segments (around 5 or 6 per show) from the Wait Wait website, but reading the URL they come from shows the server they are hosted on. Here's how the show works:

- The show is a weekly show, broadcasted every Saturday of the year (so all dates will be Saturdays).
- The URL seems to follow this general format:
```
http://public.npr.org/anon.npr-mp3/npr/waitwait/2007/01/20070113_waitwait_01.mp3
```
The example given here is the 1/13/07 show, so you can see how the date is formatted in the URL. At the end of the mp3's filename, the "_01" part, is the numbered segment of the show. Each show has different numbers of pieces, but obviously the URL doesn't exist for segment numbers that are out of bounds for that particular show.

I would ideally like to be able to run one wget command that downloads a month's worth (or a year's would be even better) of a show and places them upon downloading into appropriate directories. For instance (and it doesn't have to be this), creating a 2007 shows folder, then putting all the January shows in one folder, all the February shows in another, etc.

I've tried reading my way through the man page for wget, but I'm having a hard time coming up with a fully-automated command for this. I know this is a very unique and probably difficult question, but I didn't know where else to go, and I've always been able to find experts here.

---

### Post by wojox on 2009-08-01
Create a file Called npr.txt add this:

```
http://public.npr.org/anon.npr-mp3/npr/waitwait/2009/01/2009013_waitwait_01.mp3
http://public.npr.org/anon.npr-mp3/npr/waitwait/2009/01/20090110_waitwait_01.mp3
http://public.npr.org/anon.npr-mp3/npr/waitwait/2009/01/20090117_waitwait_01.mp3
```

Then in the terminal:

```
wget --input-file=npr.txt
```

Look in your home directory and open with mp3 player of choice.

---

### Post by alan_daniel on 2009-08-01
That works but is effectively the same as just typing in individual wget commands for each show segment, because I would have to create a file and create a line for each segment. And because a typical week's show has upwards of 8 segments, this file would need to be hundreds of lines for a year's worth of shows, which kind of defeats the purpose of trying to automate it.

Thanks for the suggestion, though. It's definitely something I can use as a last resort if I can't find something more automated.

---

