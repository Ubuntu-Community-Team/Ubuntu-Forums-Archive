---
title: "dialog box size too large"
date: 2010-05-03
forum: General Help
---

### Post by sidewalkcynic on 2010-05-03
the application that is giving me the most grief, as far as the dialog box being over-sized for the screen is KDE BasKet - how do I adjust it?

I have looked at the configuring file in the kde home file, but I am not seeing anything that looks like it controls the properties dialog box.

> [File Look]
bold=false
color=invalid
hoverColor=invalid
iconSize=32
italic=false
preview=TwiceIconSize
underlining=Never

[Insert Note Default Values]
defIconSize=32
defImageX=300
defImageY=200

[Launcher Look]
bold=true
color=invalid
hoverColor=invalid
iconSize=48
italic=false
preview=None
underlining=Never

[Local Link Look]
bold=false
color=invalid
hoverColor=invalid
iconSize=22
italic=true
preview=TwiceIconSize
underlining=OnMouseHover

[Main window]
autoBullet=true
basketTreeWidth=231
bigNotes=false
blinkedFilter=false
confirmNoteDeletion=true
enableReLockTimeout=true
exportTextTags=true
filterOnTop=false
groupOnInsertionLine=false
hideOnMouseOut=false
lastBackup=-4713,1,1
middleAction=0
playAnimations=true
position=0,0
reLockTimeoutMinutes=0
showIconInSystray=false
showNotesToolTip=true
showOnMouseIn=false
size=1024,575
spellCheckTextNotes=true
startDocked=true
timeToHideOnMouseOut=0
timeToShowOnMouseIn=1
treeOnLeft=true
usePassivePopup=true
useSystray=true
welcomeBasketsAdded=true

[MainWindow]
Height 600=601
State=AAAA/wAAAAD9AAAAAAAABAAAAAH0AAAABAAAAAQAAAAIAAAACPwAAAABAAAAAgAAAAIAAAAWAG0AYQBpAG4AVABvAG8AbABCAGEAcgEAAAAA/////wAAAAAAAAAAAAAAJgByAGkAYwBoAFQAZQB4AHQARQBkAGkAdABUAG8AbwBsAEIAYQByAQAAAsX/////AAAAAAAAAAA=
ToolBarsMovable=Disabled
Width 1024=1025

[MainWindow Toolbar mainToolBar]
IconText=IconOnly
Index=0
alreadySetToolbarSettings=true

[MainWindow Toolbar richTextEditToolBar]
Index=1
Position=Top

[Network Link Look]
bold=false
color=invalid
hoverColor=invalid
iconSize=16
italic=false
preview=None
underlining=OnMouseOutside

[Note Addition]
newNotesPlace=1
viewHtmlFileContent=0
viewImageFileContent=1
viewSoundFileContent=1
viewTextFileContent=0

[Notification Messages]
emptyBasketInfo=true

[Programs]
animationProg=gimp
animationUseProg=true
htmlProg=quanta
htmlUseProg=false
imageProg=kolourpaint
imageUseProg=true
soundProg=
soundUseProg=false

[Sound Look]
bold=false
color=invalid
hoverColor=invalid
iconSize=32
italic=false
preview=None
underlining=Never

---

### Post by sir_nasty on 2010-05-03
I'm taking a wild guess but I'd modify these settings to be within your screen resolution settings

```


[MainWindow]
Height 600=601
State=AAAA/wAAAAD9AAAAAAAABAAAAAH0AAAABAAAAAQAAAAIAAAACPwAAAA BAAAAAgAAAAIAAAAWAG0AYQBpAG4AVABvAG8AbABCAGEAcgEAA AAA/////wAAAAAAAAAAAAAAJgByAGkAYwBoAFQAZQB4AHQARQBkAGkAdAB UAG8AbwBsAEIAYQByAQAAAsX/////AAAAAAAAAAA=
ToolBarsMovable=Disabled
Width 1024=1025


```

---

