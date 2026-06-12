---
title: "Help with Festival"
date: 2011-03-02
forum: General Help
---

### Post by adam1mc on 2011-03-02
I need some help getting Festival to read a file back to me.  Nothing I have tried works and none of the information I can find on the web seems valid.

I have to say, trying to use Linux is about as painful as a hernia.  The Linux coders really should make an effort to provide VALID and useful information when writing the man pages for their apps.  It's absolutely absurd for a beginner to have to post a forum topic or conduct Google searches to learn how to do EVERY LITTLE THING when using linux -- mainly because the MAN pages are just pure junk!

Clear as day, here is the page on Festival:
[https://help.ubuntu.com/community/TextToSpeech](https://help.ubuntu.com/community/TextToSpeech)

The test works:
You will be presented with a > prompt. Type
    *  (SayText "Hello")*




To listen to a text file named FILENAME, type
   *   (tts "FILENAME" nil) *
Note FILENAME must be in quote marks. 

**DOES NOT WORK.**


[I]festival>  (tts "home/adam/Desktop/AJ.txt" nil)
SIOD ERROR:  could not open file home/adam/Desktop/AJ.txt
festival>[/I]

WTF does that mean?  Why can the file not be opened?  The file is on the desktop.  It's sitting right there.  It's just text.


Try again a bit different:
[I]festival> tts "home/adam/Desktop/AJ.txt" nil  
#<CLOSURE (file mode) (begin "(tts FILE MODE)
  Convert FILE to speech.  MODE identifies any special treatment
  necessary for FILE.  This is simply a front end to tts_file but 
  puts the system in async audio mode first. [see TTS]" (audio_mode (quote async)) (if mode (tts_file file mode) (tts_file file (tts_find_text_mode file auto-text-mode-alist))))>
"home/adam/Desktop/AJ.txt"
nil
festival> [/I]



Seriously?  Why is the documentation for Linux such junk and why do man pages (a) not provide examples (b) state their options in more clear terms  or  (c) provide understandable meaning to options?  

This is by far the absolute worst problem with Linux and unfortunately it's only the 3rd party developers who are to blame.  Does little good to write an app if no one knows how to use it.

Ug I'm frustrated.

---

### Post by adam1mc on 2011-03-02
Ug.  It finally worked after the umpteenth time.  I'm not sure what I did different.  Just typed the command a gazzillon tmies and finally it worked.

---

### Post by lykeion on 2011-03-02
Hi there
First of all I think you need to take a deep breath and relax, it's no good being frustrated when working with computers. And blaming linux as a whole for your problems is just ridiculous.

Second of all there's nothing wrong with the Ubuntu documentation of festival, it's quite straight-forward. My guess is there's wrong with your file home/adam/Desktop/AJ.txt. Could you confirm that it's a valid file by pasting output of this command:
```
cat home/adam/Desktop/AJ.txt
```

EDIT
Saw that you solved your problem by yourself, so I guess you can tag this thread as solved then.

---

