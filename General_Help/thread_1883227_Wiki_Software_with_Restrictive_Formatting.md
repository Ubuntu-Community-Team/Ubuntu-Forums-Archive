---
title: "Wiki Software with Restrictive Formatting"
date: 2011-11-18
forum: General Help
---

### Post by Joshua on 2011-11-18
Does anyone know of an open source Wiki or CMS software package that is easy to install and run on Ubuntu?

The big feature requirement I'm looking for is that I want to restrict control to a small number of people who can create pages and outline the major categories of content for those pages.  Then everyone else would be able to fill in and/or edit the content within those major categories on each page.

---

### Post by lisati on 2011-11-18
[Mediawiki]("http://www.mediawiki.org") (as used by Wikipedia) does offer some control over who can edit, but my experience is that it can be a pain poking around finding which settings to change.
[URL="http://www.dokuwiki.org"]
DokuWiki[/URL] also seems to work well with Ubuntu, and can be set to restrict editing to registered users.

---

### Post by Joshua on 2011-11-18
Those were a couple of the first two I looked at, but it wasn't clear to me if what I want would be possible.  Both of those seem to allow a good amount of access control, but I couldn't figure out how to do it at the level I need.

For example, I want an Administrative group to be able to, basically, create a data structure.  Something like:

- Topic 1
-- Data Category 1A
<content 1A>
-- Data Category 1B
<content 1B>
-- Data Category 1C
<content 1C>

- Topic 2
-- Data Category 2A
<content 2A>
-- Data Category 2B
<content 2B>
-- Data Category 2C
<content 2C>

Then, there would be a normal user group that could only edit the content, but not add Topic 3 or data category 1D.

---

