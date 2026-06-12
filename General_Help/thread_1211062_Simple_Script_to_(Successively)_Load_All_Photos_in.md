---
title: "Simple Script to (Successively) Load All Photos into GIMP (other other app) for Edit?"
date: 2009-07-12
forum: General Help
---

### Post by blissfulpenguin on 2009-07-12
Happy Sunday, Forum.

Amazingly, it has been years since I have started a thread, I think.  Usually what I need is right at my fingertips through the search feature.  I do quite a bit of photo editing, and I am very particular about the software I use.  Picasa, gThumb and the like are great, but do not offer the full advantages of the GIMP.

I still have not gotten the hang of writing scripts with variables, and perhaps now more than ever would be a good time for me to learn.  But, what I need is a simple script that will open all the files in a directory for editing, but only one at a time.  Obviously this is to prevent grinding the last breath of life from my 64-bit cpu.  Once each file closes, another should open.

It seems like I remember something about sequences from Linux Shell Scripting for Bash, but I am completely unfamiliar with the syntax.  Could anyone help?

Thanks in advance,

Yo Blip

---

### Post by geirha on 2009-07-13
Opening a new file automatically when gimp closes the previous is a bit complicated, but opening a new file when gimp exits, is doable.

```
for file in *.jpg; do gimp "$file"; done
```

---

### Post by Subban on 2009-07-13
Another suggestion that is also a bit of a workaround rather than a direct solution to your question.

In case you haven't realised in gThumb you can very, very easily add functions to keybindings. It is very simple to add one to open the Gimp when you press for example 0 on the number pad.

Open up gThumb, and open the preferences in the Edit menu. Click on the "Hot Keys" tab. In the box for 0 enter the following:

```
gimp %F
```



I also use several others, such as copy a photograph to a sub folder called "approved", this lets me very quickly sort good images from the inevitable junk ones I get:

```
mkdir -p %p/approved ; cp %f %p/approved/
```

Another is to bind a key that copies the image to a "print" folder, so I can quickly sort out images for uploading to an online photo print service, change username to your login name, and make the print folder:

```
cp %f /home/USERNAME/print/
```

One last one (rather than list all of mine), this adds the nice white border around an image with just a key press, be aware it does overwrite it:

```
convert -bordercolor white -border 50x50 %f %f
```

Just pop those commands if the are useful into the one fo the other boxes each, then when you are viewing an image you can just tap the number pad key to perform the action.

Hopefully that will be a simple way for you to open your images into the Gimp and other tricks :]

I hope that is helpful.

---

