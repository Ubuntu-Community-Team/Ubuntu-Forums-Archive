---
title: "little howto resize and rename a bunch of jpg pictures and save them in a new folder"
date: 2011-10-23
forum: General Help
---

### Post by alfonso78 on 2011-10-23
Hi,

there are a couple of pages that explain how to automatically resize a folder of pictures:
[http://ubuntuhowtos.com/howtos/resize_folder_of_pictures](http://ubuntuhowtos.com/howtos/resize_folder_of_pictures)
[http://bdhacker.wordpress.com/2011/01/04/resize-multiple-images-in-a-folder-batch-image-resize-in-ubuntu/](http://bdhacker.wordpress.com/2011/01/04/resize-multiple-images-in-a-folder-batch-image-resize-in-ubuntu/)

but I was looking for something a bit more complex:

I wanted to find all the files with jpg or JPG extension, without going in subfolders and then conver them to 50% of their size and store them in a different folder.

Here is how:

```
find ./folder/to/pics/ -mindepth 1 -maxdepth 1 -iname "*.jpg" -printf "convert -scale 50%% '%h/%f' '/path/where/to/save/small_%f' \n" | sh
```

the cool thing about this command is that if you take away the [FONT="Courier New"]**| sh**[/FONT] at the end of it, you can check what commands you're about to issue to modify it as you need.

Actually I realize that this was NOT what I wanted to do really, I wanted to make each picture fit in a max size so I found the resize command to fit my needs better:

```
find ./folder/to/pics/ -mindepth 1 -maxdepth 1 -iname "*.jpg" -printf "convert -resize 1440x900 '%h/%f' '/path/where/to/save/small_%f' \n" | sh
```

hope this helps! :)

NOTE TO SELF:
next step would be to make a script that runs on all the cores.
See:
[http://www.rootninja.com/use-multiple-processors-in-bash-by-running-commands-in-parallel/](http://www.rootninja.com/use-multiple-processors-in-bash-by-running-commands-in-parallel/)

---

