---
title: "Totem Subtitles"
date: 2009-08-01
forum: General Help
---

### Post by chmacka on 2009-08-01
I start totem from terminal and open a movie I don't see the subtitles and this is what I get in terminal:

```
** Message: don't know how to handle application/x-subrip

```Subtitle has the same name as the movie and it's, as you can see, in .srt format.

EDIT: I set up totem to automatically load subtitles.

---

### Post by moster on 2009-08-01
Maybe unsupported subtitles. Load that file in some of subtitle editors (eg. subtitle editor), save as srt and then try again.

---

### Post by chmacka on 2009-08-01
It didn't help. It works in MPlayer and in VLC.

---

### Post by moster on 2009-08-02
Subtitle editor have "check for errors" in tools menu. Try with that.

Now when I think of that prog, it has little stupid name. Why they did not gave him real unique name instead of this... Subtitle editor named subtitle editor.

---

### Post by chmacka on 2009-08-02
I never could play subtitles with Totem. I created a simple .srt test subtitle (with Subtitle Editor). I checked for errors and it didn't found any.

I attached the subtitle here. Can you download it and try to play it, so we could know if the subtitle itself is the problem or something else?

P. S.: I zipped the .srt file because .srt extension isn't allowed here.

**EDIT:** I'll say it again: it works with every other video player, so I think the subtitle isn't the problem.

---

### Post by Vaphell on 2009-08-02
sub file works for me in 8.04

do other sub formats work, for example mdvd?

---

### Post by moster on 2009-08-02
This was inside.

```
1
00:00:01,000 --> 00:00:03,000
This is just a test.

```

Do you send me this on purpose or you did not know it was nearly empty file? Why you did not send real subtitle?

I use smplayer for viewing movies because that is only player that can put subtitles bellow actual movie. On black bars. But .srt is standard format you should not have any problems in any player if is subtitle valid.

Sometimes 1 empty line is instead ov valid line and some of players confuse. That is only option why it should not load subtitle. But is did not encounter in many mounths for that.

---

### Post by chmacka on 2009-08-02
I couldn't find any real subtitles on my computer, so I made one for testing. I remember that before Totem wouldn't play any subtitles. Now I downloaded a real subtitle and it works (?). Now I understand that the subtitle has to have at least one *I-don't-know-the-word* with two lines to work with totem. Thanks, everyone!

---

### Post by moster on 2009-08-02
haha, Ok, have fun :)

---

