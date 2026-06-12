---
title: "lighttpd + authentication"
date: 2010-02-27
forum: General Help
---

### Post by senseiam on 2010-02-27
I am having some authentication issues and I can't make heads out of tails of it. Maybe someone can shed some light? Would be greatly appreciated.

Basically I want a login prompt for folder /rtorrent/ & /rtorrent1/, 2 users. I have tried both htdigest & htpasswd. For some unknown reason only the first user works (/rtorrent/) and not the second (/rtorrent1/).

There is one difference between htdigest and htpasswd I noticed. When I use htdigest both users get a login prompt, problem being no matter what password I input for user2 I get incorrect login info.

For htpasswd I only get a login prompt for the first user, second user is wide open! :o

Script I am using:

htdigest:
server.modules += ( "mod_auth" )
auth.backend = "htdigest"
auth.backend.htdigest.userfile = "/etc/lighttpd/.auth"
auth.debug = 2
auth.require = ( "/rtorrent/" =>
(
"method" => "basic",
"realm" => "Authorized users only",
"require" => "user=user1"
),
"/rtorrent1/" =>
("method" => "basic",
"realm" => "Authorized users only",
"require" => "user=user2"
)
)

htpasswd:
server.modules += ( "mod_auth" )
auth.backend = "htpasswd"
auth.backend.htpasswd.userfile = "/etc/lighttpd/htpasswd.htaccess"
auth.require = ( "/rtorrent/" =>
(
"method" => "basic",
"realm" => "Welcome user1",
"require" => "user=user1"
),
"/rtorrent1/" =>
("method" => "basic",
"realm" => "Welcome user2",
"require" => "user=user2"
)
)

---

