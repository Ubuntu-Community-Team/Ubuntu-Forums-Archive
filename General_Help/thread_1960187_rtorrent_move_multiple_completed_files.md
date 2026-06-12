---
title: "rtorrent move multiple completed files"
date: 2012-04-16
forum: General Help
---

### Post by patsissons on 2012-04-16
I have run into a problem. rtorrent sometimes downloads torrents that contain multiple files without a directory structure.  That is to say that the torrent will contain multiple files that all download to rtorrent's download folder.  I have rtorrent set up to move completed files to a completed directory, but when the torrent has multiple files in the root it can't really do that because it will try and move the whole root download directory (and obviously fail).  So i figure there's two things i can do to fix this.  either make rtorrent automatically create a download directory for these poorly constructed torrents, or alternatively just move completed files as they complete. I have no clue how to accomplish the first idea. And im unaware of any events that i can latch onto to accomplish the 2nd idea. Any thoughts on this?

---

### Post by pyroscope on 2012-04-17
This is rather uncommon to impossible, since either a metafile is single-file, or multi-file (cf. BEP-3). In the latter case, it always has a named root directory. For further investigation, I'd need to see the .torrent file (e.g. a "lstor --raw" dump).

---

### Post by patsissons on 2012-04-21
after looking through the libtorrent source code i think i figured out the issue.  The download directory is derived from the DownloadInfo's name field. That field is set by reading the torrent file.  This issue occurs on magnet uri's, which generate a very basic torrent file with that magnet uri. This basic torrent file doesn't actually contain a name field.  the magnet uri spec does allow for a display name (dn=) but im not sure if libtorrent recognizes it.

So i don't really have a solution for this issue, i only have a basic working knowledge of the rtorrent/libtorrent code and im not really sure how to inject a name into the magnet uri's easily.

for anyone interested in exploring further, the place to really look is DownloadConstructor::initialize(Object& b) in download/download_constructor.cc specifically at parse_name(b.get_key("info"));
in core/download_factory.cc the magnet uri is built with this line: *m_stream << "d10:magnet-uri" << m_uri.length() << ":" << m_uri << "e";

perhaps the best strategy is to simply parse out the display name with this regex dn=([^&]) from the uri? maybe something like this:
parse_magnet_uri(b, b.get_key_string("dn")); im not sure...

---

### Post by pyroscope on 2012-04-21
Open an issue on github, where Jari can actually see it, else it won't get fixed.

---

