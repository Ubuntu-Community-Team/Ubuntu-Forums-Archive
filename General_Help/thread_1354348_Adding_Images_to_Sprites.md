---
title: "Adding Images to Sprites?"
date: 2009-12-13
forum: General Help
---

### Post by DProg on 2009-12-13
Hey,

How would I be able to add an image to the sprite:

```
# Player class that handles Player object and movement
class Player(pygame.sprite.Sprite):
    def __init__(self):

        # create sprite
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.Surface((25, 25))
        self.image = self.image.convert()

        # Player is colored white
        self.image.fill((255, 255, 255))

        # Player sprite is a rectangle
        self.rect = self.image.get_rect()

```Also, how would I add backround music? Everytime I try to add something it freezes on me. I'm new to this so I dont know if my code is wrong or if it's another reason.

Thanks!

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
[You could google it...]("http://lmgtfy.com/?q=add+images+to+sprites")

---

### Post by DProg on 2009-12-13
> **Sin@Sin-Sacrifice said:**
> [You could google it...]("http://lmgtfy.com/?q=add+images+to+sprites")

I did...that's how I got here.

So far google hasn't really helped me.

Thanks for the effort though.

---

