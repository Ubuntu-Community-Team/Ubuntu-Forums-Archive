---
title: "Mojibake/Gibberish Encoding in MP3s/Filenames"
date: 2010-07-06
forum: General Help
---

### Post by moon2js on 2010-07-06
I've got a weird issue.

I received a zip file from a Korean friend of indie bands to sample. Problem is the mp3 filenames and ID3 data are all gibberish. I figured out how to fix the ID3 data mostly, but the filenames are still gibberish, more importantly they are a different kind of gibberish.

[INDENT]&#9553;&#937;&#9558;&#9580;&#9472;&#9612;&#9557;«&#9474;&#9577;&#9557;&#9570;&#9492;·
&#9565;¡&#9618;&#9474;&#9618;&#9579;&#9558;&#8734;&#9559;&#964;&#9488;&#949;&#9569;&#963;
&#9617;&#9570;&#9558;&#9617;&#9564;&#9500; &#9492;&#9552;&#9564;&#9553;&#9567;&#9524;&#9558;&#9571;&#9564;&#9553;[/INDENT]

Each line should be a band name.

My guess is the filesystem of the zip file and the sender's machine must use a Korean encoding by default and my machine must be unzipping the file as if it were a Western encoding. For whatever reason, this gibberish is different from the gibberish from the same issue in ID3 tags.

I renamed the files by batch using the corrected ID3 tags, but folders are still an annoying mess.

Does anyone know what I might do to preserve file and foldernames  and/or convert them to Unicode? I looked for encoding issues in man files but didn't find anything relevant.

---

