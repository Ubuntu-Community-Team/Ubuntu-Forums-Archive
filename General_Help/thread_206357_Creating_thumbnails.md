---
title: "Creating thumbnails"
date: 2006-06-29
forum: General Help
---

### Post by LanceM on 2006-06-29
I am looking for a good application to generate thumbnails from large pictures. I have, in the past, used Media Resizer on a Windows box and I am pleased with the job it does. Is there an application like that for Linux? If not, what do you use to resize large images to thumbnails?

Thanks, 
Lance

---

### Post by Keith_Beef on 2006-06-30
[QUOTE=LanceM]I am looking for a good application to generate thumbnails from large pictures. I have, in the past, used Media Resizer on a Windows box and I am pleased with the job it does. Is there an application like that for Linux? If not, what do you use to resize large images to thumbnails?

Thanks, 
Lance[/QUOTE]

Convert, part of the Image Magick package.

Here's an example of it being used in a Nautilus script. I select a few images, click with MB3 and select the script from the menu.

```

## make_thumbnail
#
# takes a new-line delimited list of files
#
# loop through the list,
#  for each file:
#   make a 180 x 180 thumbnail
#

for input_file in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
 stem=`echo $input_file | cut -f1 -d"."`
 type=`echo $input_file | cut -f2 -d"."`
 output_file=${stem}_thumb.${type}
 convert -size 180x180 $input_file -resize 180x180 +profile "*" $output_file
done

```

Beef.

---

### Post by Scruffynerf on 2007-04-17
Apologies to all by necro'ing this thread, however I've recently been trying to do something very similar to the OP, and have recently come across the 'Resize_images' Nautilis script as detailed in [Rhosgobel's site]("http://rhosgobel.blogspot.com/search/label/Linux") (The Friday, July 07, 2006 post)

cheers

Scruffy.

---

