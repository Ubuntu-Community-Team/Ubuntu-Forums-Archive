---
title: "script to automate extracting audio from video"
date: 2012-06-14
forum: General Help
---

### Post by p3aul on 2012-06-14
How could I turn this terminal command into a script(.sh) that would take an input file name and an output file name and do the extraction in the terminal?

ffmpeg -i in.flv -vn -f wav out.wav

Thanks,
Paul

---

### Post by Vaphell on 2012-06-14
```
#!/bin/sh
ffmpeg -i "$1" -vn -f wav "$2"
```


$1 and $2 are script parameters
```
./script.sh in.flv out.wav
```

---

### Post by p3aul on 2012-06-14
Thanks! ow would i use it? like this?
name.sh in.flv out.wav ?
Paul

---

### Post by Vaphell on 2012-06-14
if your script is not located in a place that is mentioned in $PATH ( try *echo $PATH*) then you need to provide the path, either absolute or relative
often you run scripts from their location - .=current dir, so ./name.sh

alternatively you can create bin directory in your home and store your custom scripts there. After logging out/logging in it should be detected and automatically added to $PATH, so you can run the script solely by its name regardless of the location you are at.

---

### Post by p3aul on 2012-06-14
Ok I am having problems. Here is my input and  here is the output
$exwav.sh cb.flv boo.wav
$Expected number for v but found: wav
I think it's choking on the second variable

---

### Post by Vaphell on 2012-06-14
if you copied my code i made a typo, your line had -f wav and i initially typed -v by mistake

---

### Post by p3aul on 2012-06-14
ok, that did it! Thanks, youve been a big help):P

I created a dialog with read statements to enter the filenames and I created a link and moved the like to the upper panel(Gnome 2) but when I tried to execute it it gave me an error:
Could Not Launch Application: Couldnot execute Child Process:

---

### Post by VCoolio on 2012-06-15
First, I'd skip the part where you have to enter the wav-filename. You just take the input filename without extension and append .wav, and also you can have the script accept multiple files: ```
#!/bin/sh
for i in "$@"; do
    ffmpeg -i "$i" -vn -f wav "${i%.*}.wav"
done
```

Paste your "read filenames" script so we can have a look. Not sure about the "child process" error.

---

