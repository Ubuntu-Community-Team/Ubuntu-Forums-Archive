---
title: "Gimp thing"
date: 2010-07-19
forum: General Help
---

### Post by 3948ctyj on 2010-07-19
say you bring a photo into Gimp and draw some straight lines
on it and save it. If you open this new image in Gimp ,how
can you just change the color of the lines....no other changes...
???  how do you do this without redrawing the whole thing..???

---

### Post by techunit on 2010-07-19
well sir first you must save it as a gimp file... you can't save it as anything else... to make different versions you could just save as *.jpg or something of that nature.

---

### Post by AlphaLexman on 2010-07-19
To expand on what techunit said, the native format for gimp files is '*.xcf' 
This format will save all layers, transparency etc.

To your question, if your were to just draw some lines with the pencil or paintbrush tool, on the SAME layer as your photo, you have over-written the pixels on that layer. (it could be undone with Crtl-z, but, if you save, close, and open the file, your undo history is gone. However, you could select by color and change the color of the pencil or paintbrush marks from the previous edit.

You would be better off creating a new layer above the photo layer, and making your pencil or paintbrush marks there. It will not overwrite any pixels on the photo layer below. Then the color could be changed much easier as it is on it's own layer.

---

