---
title: "Photo rotation"
date: 2011-01-10
forum: General Help
---

### Post by hornetster on 2011-01-10
Have a stack of photos - some long edge horizontal, others long edge vertical - and linux seems to "double guess" and display them the correct way, which is great, to a point... :confused:
Problem comes when I then want to put them on a web page and they ALL become long edge horizontal.
How, and with what program, can I force the orientation so I know they will be correct wherever they are viewed?
Did find a couple of other threads with the question, but no real solution..
Thanks, John.

---

### Post by coldraven on 2011-01-10
The simplest way is to rotate them as you view them.
When I double click an image the "Eye of Gnome" image viewer opens.
Select Edit>Rotate then File>Save.
The image is now permanently rotated.

If you have hundreds of images the download Phatch from the Software center.
Create a filter in Phatch to rotate an image clockwise.
Copy all the images needing clockwise rotation into a directory called "/turn-right".
Run Phatch on that directory and optionally copy them back to where they came from. 
Check the results before overwriting the original images!!!
Do the same for the other orientation.

---

### Post by tredegar on 2011-01-10
**ImageMagic** has a good set of tools for manipulating pictures.

Sometimes the image can be correctly displayed if there is suitable **exif** data attached to the image, and it is read and acted on by whatever is used to display the image.

**jhead** is used to display and manipulate data contained in the Exif header of JPEG images from digital cameras. See **man jhead**
**jhead -autorot pic.jpg** is probably what you should look at.

Hope this points you in the right direction.

---

### Post by hornetster on 2011-01-10
Thanks for the replies. My issue is that when i take a photo "on its side", as soon as I copy it to Ubuntu, it seems that most of the photo apps, including nautilus, displays them all correctly (clever camera/Ubuntu...?)
But it's a PITA, as you can't tell by default whether the photo is oriented correctly, or not. The meta data doesn't seem to tell you either.
The only way I can tell (just did a test) is, for example, open the picture in gThumb and select rotate. If the picture still looks the same, it is now the correct orientation, if it's now lying on its side, it was correct before....
Please correct me if I'm wrong....
Thanks, John.

---

### Post by veggen on 2011-01-10
Hmm, there probably is an option in every image viewer to **not** use EXIF data do determine orientation (which must be what it's doing). Try looking for it...
Also, tredegar's idea about jhead sounds like it might help automate "rotation" (EXIF data change actually).

---

### Post by tredegar on 2011-01-10
> Also, tredegar's idea about jhead sounds like it might help automate "rotation"
Correct, but it rotates the image if necessary, and *then* updates the Exif information to reflect that. 

From the man page (and I *know* people don't like to read the information that is already there)
> [B]-autorot
[/B]
    Using the 'Orientation' tag of the Exif header, rotate the image so that it is _upright_. The program **jpegtran** is used to perform the rotation. This program is present in most Linux distributions.  After rotation, _the orientation tag of the Exif header is set to '1' (normal orientation)_. The thumbnail is also rotated. Other fields of the Exif header, including dimensions are untouched, but the JPEG height/width are adjusted. This feature is especially useful with newer cameras, that set the orientation tag automatically using a gravity sensor. 

"You can lead a horse to water, but you cannot make it drink".

---

### Post by hornetster on 2011-01-11
Why is this so difficult? Have never had/ (noticed??) this issue before using openSuse (and KDE) for several years... 
Just looked through all the graphics progs I have installed in 10.10 (fspot, gthumb, gimp, shotwell and image viewer(?) ) and the only program where I can figure out the *correct* orientation of a photo is gimp...
Can't determine this in any of the menus/metadata of any of the other programs. 
Is Ubuntu TOO clever?
Thanks, John.

---

### Post by coldraven on 2011-01-13
Well 10.10 is not smart enough to rotate images on my PC!
However, my camera is fairly old so I guess the EXIF data has less info than yours.
I've searched through gconf and compiz settings but cannot find anything that would auto-rotate your images.
Somebody must know why!

---

