---
title: "OpenGL audio problems"
date: 2006-04-12
forum: General Help
---

### Post by WillisBueller on 2006-04-12
Hello. I'm currently setup using alsa, i have 2 sound cards in my computer. Audio works fine for regular apps, amarok, VLC, that sort of stuff. But I can't get audio in any openGL games (tuxracer, torcs) or SDL games.Any ideas? thanks

---

### Post by WillisBueller on 2006-04-12
Ok, after further research i think the problem is either with OpenAL or SDL. I have two soundcares, am using hw:1,0
here is my .openalrc

(define devices '(alsa sdl native oss))
(define speaker-num 2)
(define alsa-out-device "hw:1,0")
(define alsa-in-device &#8220;hw:1.0&#8221;)

---

