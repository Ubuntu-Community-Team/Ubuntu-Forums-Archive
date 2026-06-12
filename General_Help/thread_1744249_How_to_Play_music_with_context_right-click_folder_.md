---
title: "How to Play music with context right-click folder menu ?"
date: 2011-04-30
forum: General Help
---

### Post by talofo on 2011-04-30
Hello all,

I wish to right click on a folder, and choose play to play all files inside that folder, including ones inside subfolders as well (if any).

I've placed this play ruby file here:
~/.gnome2/nautilus-scripts


```
#!/usr/bin/env ruby1.9.1
require 'find'

PLAYER = "banshee"
PLAYER_OPTIONS = ["--play-enqueued"]

def play *f
    IO.popen [PLAYER, *PLAYER_OPTIONS, *f] do |io|
        io.read
    end
end

def is_audio f
    begin
        io = IO.popen ['file', '--mime-type', f]
        op = io.read.split(' ')
        r = op[op.length-1] =~ /audio/
        io.close
        r
    rescue
    end
end

files = []

ARGV.each do |f|
    if File.directory? f
        Find.find f do |f|
            files << f if is_audio(f)
        end
    else
        files << f if is_audio(f)
    end
end

play(*files)
```

But when I Right-Click > Scripts > Play 

Banshee doesn't even get open. 


Is there another way for archiving this ?


Thanks

---

