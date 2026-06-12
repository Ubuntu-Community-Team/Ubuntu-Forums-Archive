---
title: "bzr error following serverguide instructions"
date: 2012-01-07
forum: General Help
---

### Post by Lars Noodén on 2012-01-07
This is my first time using **bzr**.  There's something wrong with the instructions for editing the [url=https://wiki.ubuntu.com/DocumentationTeam/SystemDocumentation/UbuntuServerGuide
]server guide[/url].  I am getting errors when trying to push my changes:

```

$ bzr push lp:~larsnooden/serverguide/serverguide-review-6.1
You have not informed bzr of your Launchpad ID, and you must do this to write to Launchpad or access private data.  See "bzr help launchpad-login".
bzr: ERROR: Invalid url supplied to transport:
"bzr+ssh://bazaar.launchpad.net/~larsnooden/serverguide/serverguide-review-6.1":
no supported schemes

```

After I use **bzr whoami**, the error changes:

```

$ bzr push lp:~larsnooden/serverguide/serverguide-review-6.1
Permission denied (publickey).
ConnectionReset reading response for 'BzrDir.open_2.1', retrying
Permission denied (publickey).
bzr: ERROR: Connection closed: Unexpected end of message. Please check
connectivity and permissions, and report a bug if problems persist.

```

How do I move the changes I have made to my Launchpad Account?

---

### Post by Lars Noodén on 2012-01-07
It turns out there is a bug in **bzr** or in Launchpad.  The SSH key needed a password and I was not getting queried for the password.  The work around was to use a key agent and load the key into the agent before trying the command.  This was not covered in the documentation.

---

