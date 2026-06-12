---
title: "Gimp batch mode help"
date: 2011-01-03
forum: General Help
---

### Post by J V on 2011-01-03
I want a simple short gimp batch script that will take one image, paste it into a predetermined layer on another image, export as png and discard changes.

Unfortunately, I can't find any tutorials on using gimp batch. Anyone know any such tutorials (Or better yet, what my script needs to be)

So far this is what I have. I need a way to loop through the layers to check the name of them, I also need a way to ditch the previously opened files from memory (Otherwise  gimp still has both images in memory) (I'm going to mark this solved so I can make a cleaner post once I get it together)

```
(define (script-fu-uc-sig)

(let*
    (
        (
            workspaceImage (car (gimp-xcf-load 0 "/home/j/Pictures/forums et al/unchartedsig/unchartedsig.xcf" "unchartedsig.xcf"))
        )
        (
            inputImage (car (file-png-load RUN-NONINTERACTIVE "/home/j/Pictures/forums et al/unchartedsig/Jonavoly.png" "Jonavoly.png"))
        )
    )
    
    (gimp-selection-all inputImage)
    (gimp-edit-copy
        (vector-ref (cadr (gimp-image-get-layers inputImage)) 0 )
    )

    (gimp-edit-paste 
        (vector-ref 
            (cadr (gimp-image-get-layers workspaceImage))
            (- (car (gimp-image-get-layers workspaceImage)) 2)
        )
    workspaceImage)

    (file-png-save
        RUN-NONINTERACTIVE
        workspaceImage
        (car (gimp-image-flatten workspaceImage))
        "/home/j/Pictures/forums et al/unchartedsig/out.png"
        "out.png"
        0 9 1 0 0 1 1
    )

)
"Finished"
)

(script-fu-register
    "script-fu-uc-sig"
    "Uc stats card"
    "Uc stats card hacker, NOT FOR MANUAL USE"
    "Jonavoly"
    "GPL3"
    "January 4, 2011"
    ""
  )
```

---

### Post by J V on 2011-01-04
bumpzor

---

