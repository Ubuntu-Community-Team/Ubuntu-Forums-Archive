---
title: "Found Dungeons of Daggorath!!  But it won't compile - any help appreciated"
date: 2009-11-27
forum: General Help
---

### Post by jimmy the saint on 2009-11-27
Hey everyone

I found Dungeons of Daggorath, which is a game I enjoyed as a kid.  A linux port was released in 2003 so I figured I'd give it a go.  I have not compiled many packages myself so and I cannot figure out what is going wrong here.  I will go ahead and give the output here in some code tags as well as include a link to the .tar file.  If anyone else either wants to try in order to help me out or to play it themselves I would appreciate the assistance.

```
bluto@ubu-timeline:~/Dungeons/dod0.4.0/src$ make
In file included from creature.h:20,
                 from creature.cpp:17:
dod.h:23:17: error: SDL.h: No such file or directory
dod.h:24:24: error: SDL_opengl.h: No such file or directory
dod.h:25:23: error: SDL_mixer.h: No such file or directory
In file included from creature.h:20,
                 from creature.cpp:17:
dod.h:71: error: ‘GLfloat’ does not name a type
dod.h:77: error: ‘GLfloat’ does not name a type
dod.h:83: error: ‘GLfloat’ does not name a type
dod.h:89: error: ‘GLfloat’ does not name a type
dod.h:343: error: ‘Uint32’ does not name a type
dod.h:344: error: ‘Uint32’ does not name a type
dod.h:345: error: ‘Uint32’ does not name a type
dod.h: In member function ‘void Task::setValues(int, int, long int, long int, long int, long int, bool)’:
dod.h:356: error: ‘frequency’ was not declared in this scope
dod.h:357: error: ‘prev_time’ was not declared in this scope
dod.h:358: error: ‘next_time’ was not declared in this scope
dod.h: In member function ‘void Task::clear()’:
dod.h:366: error: ‘frequency’ was not declared in this scope
dod.h:367: error: ‘prev_time’ was not declared in this scope
dod.h:368: error: ‘next_time’ was not declared in this scope
dod.h: At global scope:
dod.h:512: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
dod.h:512: error: expected ‘;’ before ‘*’ token
In file included from creature.cpp:17:
creature.h:45: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
creature.h:45: error: expected ‘;’ before ‘*’ token
creature.h:46: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
creature.h:46: error: expected ‘;’ before ‘*’ token
creature.h:47: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
creature.h:47: error: expected ‘;’ before ‘*’ token
creature.h:48: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
creature.h:48: error: expected ‘;’ before ‘*’ token
In file included from creature.cpp:20:
object.h:50: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
object.h:50: error: expected ‘;’ before ‘*’ token
In file included from creature.cpp:21:
sched.h:41: error: ‘SDL_keysym’ has not been declared
sched.h:47: error: ‘SDL_keysym’ has not been declared
sched.h:67: error: ‘Uint32’ does not name a type
sched.h:68: error: ‘Uint32’ does not name a type
sched.h:70: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
sched.h:70: error: expected ‘;’ before ‘*’ token
In file included from creature.cpp:22:
viewer.h:92: error: ‘Uint32’ does not name a type
viewer.h:117: error: ‘GLfloat’ does not name a type
viewer.h:118: error: ‘GLfloat’ does not name a type
In file included from creature.cpp:23:
player.h:89: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
player.h:89: error: expected ‘;’ before ‘*’ token
player.h:90: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
player.h:90: error: expected ‘;’ before ‘*’ token
player.h:91: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
player.h:91: error: expected ‘;’ before ‘*’ token
In file included from creature.cpp:24:
oslink.h:59: error: ‘Uint16’ does not name a type
oslink.h:65: error: ‘SDL_keysym’ has not been declared
creature.cpp: In member function ‘void Creature::Reset()’:
creature.cpp:65: warning: deprecated conversion from string constant to ‘char*’
creature.cpp:66: warning: deprecated conversion from string constant to ‘char*’
creature.cpp: In member function ‘void Creature::LoadSounds()’:
creature.cpp:80: error: ‘creSound’ was not declared in this scope
creature.cpp:80: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:81: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:82: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:83: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:84: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:85: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:86: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:87: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:88: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:89: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:90: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:91: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:92: error: ‘clank’ was not declared in this scope
creature.cpp:92: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:93: error: ‘kaboom’ was not declared in this scope
creature.cpp:93: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp:94: error: ‘buzz’ was not declared in this scope
creature.cpp:94: error: ‘LoadSound’ is not a member of ‘Utils’
creature.cpp: In member function ‘void Creature::CBIRTH(dodBYTE)’:
creature.cpp:205: error: ‘struct Task’ has no member named ‘frequency’
creature.cpp: In member function ‘int Creature::CREGEN()’:
creature.cpp:251: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:252: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:253: error: ‘struct Task’ has no member named ‘frequency’
creature.cpp: In member function ‘int Creature::CMOVE(int, int)’:
creature.cpp:336: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:336: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:342: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:342: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:354: error: ‘creSound’ was not declared in this scope
creature.cpp:354: error: ‘Mix_PlayChannel’ was not declared in this scope
creature.cpp:355: error: ‘Mix_Playing’ was not declared in this scope
creature.cpp:357: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:357: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:365: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:365: error: ‘SDL_GetTicks’ was not declared in this scope
creature.cpp:406: error: ‘clank’ was not declared in this scope
creature.cpp:407: error: ‘Mix_Playing’ was not declared in this scope
creature.cpp:409: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:409: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:417: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:417: error: ‘SDL_GetTicks’ was not declared in this scope
creature.cpp:427: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:427: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:465: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:465: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:471: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:471: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:511: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:511: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:517: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:517: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:551: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:551: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:557: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:557: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:573: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:573: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:579: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:579: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp: In member function ‘bool Creature::CWALK(dodBYTE, CCB*)’:
creature.cpp:710: error: ‘Mix_SetPanning’ was not declared in this scope
creature.cpp:713: error: ‘MIX_MAX_VOLUME’ was not declared in this scope
creature.cpp:713: error: ‘Mix_Volume’ was not declared in this scope
creature.cpp:714: error: ‘creSound’ was not declared in this scope
creature.cpp:714: error: ‘Mix_PlayChannel’ was not declared in this scope
creature.cpp:715: error: ‘Mix_Playing’ was not declared in this scope
creature.cpp:717: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:717: error: ‘struct Task’ has no member named ‘next_time’
creature.cpp:721: error: ‘class Scheduler’ has no member named ‘curTime’
creature.cpp:721: error: ‘SDL_GetTicks’ was not declared in this scope
make: *** [creature.o] Error 1
```

[http://mspencer.net/daggorath/builds/DungeonsOfDaggorath0.4.0.tar.gz](http://mspencer.net/daggorath/builds/DungeonsOfDaggorath0.4.0.tar.gz)

Thanks Everyone!

---

