---
title: "last.fm scrobble in songbird broken"
date: 2009-12-21
forum: General Help
---

### Post by nkobel003 on 2009-12-21
When I attempt to log in to Last.fm via Songbird's Last.fm plugin, it hangs up and does not log me in, and I am therefore unable to 'scrobble' my music. Here is the interesting output in the terminal:
> clearing session
web cookies cleared
LOGIN PHASE: authorisation token request
auth.getToken SUCCESS: 7aca26d45e9128d0502070f6c9ae42f5
LOGIN PHASE: last.fm website login
webLogin SUCCESS
LOGIN PHASE: application authorisation
api grantAccess SUCCESS
LOGIN PHASE: session request
auth.getSession: FAILED TO AUTH. TOKEN: <?xml version="1.0" encoding="utf-8"?>
<lfm status="failed">
<error code="14">This token has not been authorized</error></lfm>

Any ideas? :confused:

---

### Post by scouser73 on 2009-12-21
Have you updated to Songbird 1.4.1?

---

### Post by nkobel003 on 2009-12-23
Yes, today, with a similar error:

> clearing session
web cookies cleared
LOGIN PHASE: last.fm geo-detection for weblogin
Geo login URL: [https://www.last.fm/login](https://www.last.fm/login)
Geo base domain: [www.last.fm](www.last.fm)
webLogin SUCCESS
LOGIN PHASE: authorisation token request
auth.getToken SUCCESS: f6b759740b6029bf74c8da55e53b11ca
api grantAccess URL: [http://www.last.fm/api/grantAccess](http://www.last.fm/api/grantAccess)
LOGIN PHASE: application authorisation
api grantAccess SUCCESS
LOGIN PHASE: session request
auth.getSession: FAILED TO AUTH. TOKEN: <?xml version="1.0" encoding="utf-8"?>
<lfm status="failed">
<error code="14">This token has not been authorized</error></lfm>


---

### Post by nkobel003 on 2009-12-23
Ahh, I've got it!

Under Edit>Preferences>Privacy, make sure the "Accept Third-Party Cookies" ticker is CHECKED. If this is not checked, then last.fm cannot authenticate the session.

---

