---
title: "EasyTag and Album Artist field"
date: 2011-06-11
forum: General Help
---

### Post by Condor Cluster on 2011-06-11
Trying to sort out a compilation album I downloaded, all the fields are complete apart from Album Artist.

I have the Artist field complete, but in previous albums I've tagged them as Various Artists (using iTunes).

Is it possible to somehow edit the Album Artist field in EasyTag?

Thanks.

---

### Post by nothingspecial on 2011-06-11
I don't know how to do that in easytag, however the "iTunes compilation" field can be tagged with puddletag, which unfortunately is not available in the ubuntu repos (as far as I know).

To install it
```

wget http://sourceforge.net/projects/puddletag/files/puddletag_0.10.6-1_all.deb
```

```
sudo dpkg puddletag_0.10.6-1_all.deb
```

Then (if you get errors)
```

sudo apt-get install -f
```

Open it up and browse to your compilation. Select all your songs in the right hand frame.

On the bar go Edit > Extended Tags

Press the + button and in the dropdown field box search for "itunescompilationflag". Select it and give it a value of 1.

I find puddletag better than eastag.

---

### Post by coffeecat on 2011-06-11
> **Condor Cluster said:**
> Trying to sort out a compilation album I downloaded, all the fields are complete apart from Album Artist.

I have the Artist field complete, but in previous albums I've tagged them as Various Artists (using iTunes).

Is it possible to somehow edit the Album Artist field in EasyTag?

Thanks.

I'm not quite sure what you're saying here. You have all the fields complete except the Artist one, but then you say that you have the Artist field complete.

Whatever, from the EasyTag menu, Scanner > Process Fields. Click on the Artist button and use the 3rd choice. However, I can only change a defined string into another string. If the field is already blank, it won't work and if there are different strings in that field in different tracks of the album, I haven't found a wildcard that works. Is that what you mean?

---

### Post by Condor Cluster on 2011-06-11
Installed puddletag with:

sudo add-apt-repository ppa:webupd8team/puddletag
sudo apt-get update
sudo apt-get install puddletag

Didn't use "itunescompilationflag" as that wasn't really what I was after.

I went to 'Extended Tags' in puddletag, and then manually created another field called 'Albumartist' for all the tracks in the compilation album, and set it's value to 'Various Artists'

Cheers.

---

