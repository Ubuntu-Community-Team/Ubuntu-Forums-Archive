---
title: "Please help pygame problem"
date: 2009-07-10
forum: General Help
---

### Post by farhanshahid2009 on 2009-07-10
when i load the following lines of code  from  a.py file   

import pygame,sys,os
from pygame.locals import *
dir(pygame)
pygame.init()
pygame.init()
window=pygame.display.set_mode((640,480))
pygame.display.set_caption('game')
screen=pygame.display.get_surface()
file1=os.path.join('Desktop','1.gif')
pygame.image.load(file1)
screen.blit=(file1,(0,0)) 
pygame.display.flip() 

the following error message is generated :

open /dev/sequencer: No such file or directory
Traceback (most recent call last):
  File "/home/farhan/Desktop/game.py", line 11, in ?
    screen.blit=(file1,(0,0))
AttributeError: 'pygame.Surface' object attribute 'blit' is read-only

So what do i do PLEASE HELP

---

### Post by t4thfavor on 2009-07-10
you can only read screen.blit, what is the method supposed to do?

Perhaps you can modify that source in wherever screen.blit lives to have a set property.

---

### Post by t4thfavor on 2009-07-10
Perhaps something like this, from
[http://www.pygame.org/docs/tut/MoveIt.html](http://www.pygame.org/docs/tut/MoveIt.html)

 screen = pygame.display.set_mode((640, 480))
player = pygame.image.load('player.bmp').convert()
background = pygame.image.load('background.bmp').convert()
screen.blit(background, (0, 0))
objects = []
for x in range(10): 		#create 10 objects...    
o = GameObject(player, x*40, x)
  objects.append(o)
while 1:
for event in pygame.event.get():
      if event.type in (QUIT, KEYDOWN):
           sys.exit()
      for o in objects:
      screen.blit(background, o.pos, o.pos)
      for o in objects:
         o.move()
      screen.draw(o.image, o.pos)
    pygame.display.update()
    pygame.time.delay(100)

---

