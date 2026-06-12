---
title: "Scite Question"
date: 2009-09-30
forum: General Help
---

### Post by Porter200el on 2009-09-30
Hello all,

I am using Scite (which is close to Notepad ++ for windoze), I just switched to Ubuntu 9.04 exclusively after being a windoze user for 15 years.  I am a programmer, so that being said, I am very picky about things.  With Notepad ++ I can click on a file (.php, .cfm, .html...etc) and it will open in a new tab in Notepad ++, in Scite it opens in a new instance of Scite instead of a new tab.  I googled this but couldn't find the answer, I found some help about going into the SciteGlobalConfiguration but it did not work, so your assistance is greatly appreciated.


Thanks,

Porter

---

### Post by Porter200el on 2009-09-30
Well, I did find the solution, you can edit the global config:

code.page=65001
output.code.page=65001
tabsize=4
indent.size=4
use.tabs=1
use.monospaced=1
autocompleteword.automatic=1
toolbar.visible=0
save.session=1
view.whitespace=1
view.indentation.whitespace=1
view.indentation.guides=1
highlight.indentation.guides=1
strip.trailing.spaces=1
ensure.final.line.end=1
default.file.ext=.py
time.commands=1
position.width=-1
position.height=-1
split.vertical=0
load.on.activate=1
are.you.sure.on.reload=1
reload.preserves.undo=1
backspace.unindents=1
eol.mode=LF
eol.auto=1
font.monospace=font:Consolas,size:11
start.in.monospaced.mode=1

---

