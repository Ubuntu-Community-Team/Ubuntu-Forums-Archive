---
title: "Gtk2Hs Compile Error."
date: 2010-03-03
forum: General Help
---

### Post by bhencetotozo on 2010-03-03
Hello there guys,

I am trying this new compiler, and I am having trouble with it, never tryed it before.

I installed Gtk+,Gtk2hs,and the compiler is good.

This is my glade file: 1.glade
This is my HS file:    new.hs

```
module Main where

import Graphics.UI.Gtk
import Graphics.UI.Gtk.Glade

main = do
initGUI
Just xml    <- xmlNew "1.glade"
window      <- xmlGetWidget xml castToWindow "window1"
onDestroy window mainQuit
closeButton <- xmlGetWidget xml castToButton "button2"
onClicked closeButton $ do
widgetDestroy window
label       <- xmlGetWidget xml castToLabel "label1"
entry       <- xmlGetWidget xml castToEntry "entry1"
applyButton <- xmlGetWidget xml castToButton "button1"
onClicked applyButton $ do
name <- get entry entryText
set label [ labelText := "Hello " ++ name ]
widgetShowAll window
mainGUI
```

I tryed the command as normal, and root.

ghc --make 1.hs -o 2test


Error =

```
[1 of 1] Compiling Main             ( new.hs, new.o )

new.hs:17:0:
    Couldn't match expected type `()'
           against inferred type `ConnectId Button'
      Expected type: IO ()
      Inferred type: IO (ConnectId Button)
    In the expression:
          onClicked applyButton
        $ do name <- get entry entryText
             set label [labelText := "Hello " ++ name]
             widgetShowAll window
             mainGUI
    In the second argument of `($)', namely
        `do widgetDestroy window
            label <- xmlGetWidget xml castToLabel "label1"
            entry <- xmlGetWidget xml castToEntry "entry1"
            applyButton <- xmlGetWidget xml castToButton "button1"
            ....'

```



Does any body have an idea why the program didn't compile?
This was actually a sample I found online. I tryed it, I do not understand the error. Any ideas>? PLeaseee

Thank you so much.

---

