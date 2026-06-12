---
title: "I have finaly cutaway"
date: 2009-10-08
forum: General Help
---

### Post by Extremeshannon on 2009-10-08
I officially have no winblows running at my house. I need a little help with which applications I should use and a little scripting.

1.) I have AVI's and other video files I need to be able to join. I use avimerge -o Big.avi -i video1.avi video2.avi I would like to script this with all my videos and have them get delete afterwards. The part I am worried about is deleting the videos before they are joined of if something fails. Any help would be great.

2.) Web page creation, publishing, testing etc. I am not the worlds strongest at web creation but I do my fair share. I do use dreamweaver sometimes and like that.

3.) A powerful text editor. Line numbers, code, tabs etc.. something like ultimate text

4.) Resizing of pics. I have a very small program in windows and all I have to do is right click on file or folder and say resize pic what to resize and it does the rest. Something like that.

5.) Best way for my iPhone and iPods to sync. I have seen lots on this still not sure what to do about it.

of course there will be more but those are want I need to make my life whole again. Thanks for any help.

---

### Post by MelDJ on 2009-10-08
for question 2: there is kompozer which is available in the repositories 
for 5: songbird with the ipod support add on

---

### Post by MelDJ on 2009-10-08
[quote=warduria;8070864]Sorry for nothing helpful. God bless you.
_______________________________________

if you have nothing to say, dont say anything then

---

### Post by stinger30au on 2009-10-08
> **Extremeshannon said:**
> I officially have no winblows running at my house. I need a little help with which applications I should use and a little scripting.

1.) I have AVI's and other video files I need to be able to join. I use avimerge -o Big.avi -i video1.avi video2.avi I would like to script this with all my videos and have them get delete afterwards. The part I am worried about is deleting the videos before they are joined of if something fails. Any help would be great..


use cat

man cat 

will tell all

---

### Post by mechro on 2009-10-08
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

---

### Post by Extremeshannon on 2009-10-08
Thanks everyone for the help.

---

### Post by mike555 on 2009-10-08
For resizing get "Nautilus-image-converter" , you will be able to just rt. click an image and resize .

---

### Post by pythonscript on 2009-10-08
Sorry, this is only for files that are split at the binary level. Sorry about the mix up.

---

### Post by jerome1232 on 2009-10-08
> **Extremeshannon said:**
> 

3.) A powerful text editor. Line numbers, code, tabs etc.. something like ultimate text.

The default text editor gedit does all of this. Emacs and/or Vim are popular for being great powerful text editors.

I'm pretty positive cat file > file2 will delete the contents of file2 and replace it with the contents of file. 

cat file >> file2 will append the contents of file to the end of file2.

None of it will work anyways, avi files have metadata that describes the codec and etc of the video and audio. Avidemux can be used from the command line, so to automate this process you will need to make a bash script that does the work for you. ffmpg is another powerful video transcoder that you might want to look at.

---

