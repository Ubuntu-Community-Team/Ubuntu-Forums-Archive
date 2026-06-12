---
title: "Allegro - Instalation help"
date: 2010-02-20
forum: General Help
---

### Post by Leo Sagashi on 2010-02-20
Well, here goes my trip:
After some weeks trying to successfully install and configure an IDE that could provide me some "environment" that could ease the hard work of making some games with Allegro, I was forced to give up, since I could not get my compiler to recognize those libraries (I've tried Dev-C++, Code::Blocks, etc. with both Borland C++ Compiler and MinGW). This makes me wonder how do someone learn C++, since I can not even get an IDE working with some external crap.
Since I'm a big ubuntu fan, I decided to move once again to Linux platform and tried to setup Code::Blocks with Karmic, in order to once again install Allegro libraries and make some C++ lines. Guess what?
This is PERFECTLY what I did, and I want to know where I'm wrong:
1st Step: Installed Code::Blocks, through the Control Center;
2st Step: typed "sudo apt-get install liballegro4.2-dev" Done!;
3nd Step: typed "sudo apt-get install g++" since I didn't know ubuntu don't come with G++ compiler. Done!;
4rd Step: started a project and tried to pass as flags: "allegro-config --libs" to the linker. No success, G++ doesn't recognized allegro-config;
5th Step: changed the linker flag to -lalleg. Now, G++ finally recognized it, but returned hundreds of exceptions my log doesn't even showed all.
As you can see, I'm not a real pro at C++ programming, but I have a LOT OF PATIENCE, and would like to recieve some aid from you. I'll be trying for this whole week to fix this, but I'm really going out of hope. C++ definitively seems to don't be for small hobbists like me.
P.S.: My english is bad, I know.

---

