---
title: "Get rid of Audiobooks and Podcasts folders permanently?"
date: 2010-10-17
forum: General Help
---

### Post by devondashla on 2010-10-17
In my maverick installation, I use Banshee from the latest PPA. I keep getting these folders in my Home folder for Audiobooks and Podcasts-I delete them as they're pointless to me, but they keep coming back. I even disabled podcasts and audiobooks in banshee. Is there a way to permanently get rid of these folders?

---

### Post by lolobu on 2010-11-20
With gconf-editor, go into apps->banshee-1->souces
Then in _audiobook_library_souce_-_audiobook_library, untick expanded
And in podcast_souce_-_podcats_library, untick expanded
Then you delete those directory and they won't be recreated.
Or alternatively, you can change the Audiobooks and Pocasts directory location here.

---

