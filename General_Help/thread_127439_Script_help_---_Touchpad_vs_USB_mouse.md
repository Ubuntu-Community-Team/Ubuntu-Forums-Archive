---
title: "Script help --- Touchpad vs USB mouse"
date: 2006-02-08
forum: General Help
---

### Post by greenwom on 2006-02-08
Lo! all

I'm trying to run a script that will toggle the touchpad on my Sony Vaio on/off.

This is what I've gathered from the "google realm"

```
#!/bin/bash
# My usb mouse touchpad disable scripts
def modprobe(nrmatches)
modulename="psmouse"
if (nrmatches > 0)
puts "Uninstalling #{modulename}"
`sudo modprobe -r #{modulename}`
else
puts "Installing #{modulename}"
`sudo modprobe #{modulename}`
end
end
```

Right now it doesn't work, if anyone has a word of help I'd be a happy camper

psmouse in the right module.   :rolleyes:

---

### Post by kabus on 2006-02-10
I think your problem is that this isn't a bash script.
Looks more like Ruby to me.
Install Ruby and then replace "#!/bin/bash" with "#!*/path/to/ruby*".
Not sure if this will be enough to make it work though.

---

### Post by greenwom on 2006-02-10
Thanks, I went back and looked at the two web pages and a thread here at Ubuntuforums and guess what.... your right Ruby script.

I'll post an edit giveing credit to the dude who wrote it and toss some key search words in it.  I found it a bit hard to find the fix, I'll also try to toss an icon I made for the gnome panel.

---

