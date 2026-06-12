---
title: "idl-problem visualization image"
date: 2010-05-19
forum: General Help
---

### Post by ornitorinco.f on 2010-05-19
I have a problem with idl 7.0.
When i read an image and i try to view this on a window, it give me an image 
of the dimension of my pc screen, the image is cut.
And the same happen when i write it on a file.

[I][COLOR=Blue]"read_jpeg,path_image, image

window, 10, xsize=5950, ysize=341
tv, congrid(mercury_map, 5950, 341)

image=tvrd(true=3)
tv,image,true=3

write_jpeg, path_out+'prova.jpg',image,true=3, quality=100[/COLOR][/I][COLOR=Blue]"

[COLOR=Black]With win xp, i use the same and all is ok.
Why with ubuntu change?
How i can solve this problem?

Thanks 


[/COLOR][/COLOR]

---

