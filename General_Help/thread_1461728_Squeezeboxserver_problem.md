---
title: "Squeezeboxserver problem"
date: 2010-04-24
forum: General Help
---

### Post by svsig on 2010-04-24
I have installed squeezeboxserver on my Ubuntu 9.10 server. Recently it stopped working, I don't know what happened. I have not done anything with squeezeboxserver directly so it must come from some upgrade. I can can reach the web interface and do a rescan of my music library, but I am unable to play the music from the web interface. When I click an album or track nothing happens.

I tried to purge squeezeboxserver from my server and reinstall it, but I got several error messages and it didn't work properly. Then I tried to locate all files connected to squeezeboxserver and delete them manually, hoping that I then would be able to do a clean install. But I was totally wrong of course. Now nothing works and I can't even access the web interface. And I am not able to remove it from my system with apt.

Does anybody have a solution to this? What can I do to manually get completely rid of squeezeboxserver om my system and then reinstall it?

Regards,
Sveinung

---

### Post by Brandon Williams on 2010-04-27
Most importantly ... don't try to do the work of dpkg yourself. Unless you really know what you're doing, you will miss something that might even put you into the situation where you cannot install anything anymore. Always figure out what is wrong with the specific package and apply fixes that allow you to eventually use dpkg or apt to get rid of the package. I think you've already learned this lesson, but it felt important to stress the point.

Anyway, I assume that your system still thinks squeezeboxserver is installed, is that correct? What happens when you run 'sudo aptitude purge squeezeboxserver'? Knowing the error messages will help with a solution. Also, have you tried to reinstall so that you can then attempt to purge again? Does 'sudo aptitude reinstall squeezeboxserver' work for you? If not, what's the error message?

You might have to download the original squeezeboxserver package and manually unpack the files into the correct locations in order to attempt the purge again. Try the other stuff first, though.

---

