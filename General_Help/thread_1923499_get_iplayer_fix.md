---
title: "get_iplayer fix"
date: 2012-02-10
forum: General Help
---

### Post by nikonian on 2012-02-10
For those people having trouble with "get_iplayer" version 2.80, I have found a new SWF URL which you need to replace the existing one with, inside:

```

/usr/bin/get_iplayer

```Open the above file as root, with gedit, and edit the SWF URL in red:

```

my $conn = {
            swfurl        => "[COLOR=Red]http://www.bbc.co.uk/emp/revisions/18269_21576_10player.swf?revision=18269_21576[/COLOR]",
            ext        => $ext,
            streamer    => $streamer,
            bitrate        => $mattribs->{bitrate},
            server        => $cattribs->{server},
            identifier    => $cattribs->{identifier},
            authstring    => $cattribs->{authString},
            priority    => $cattribs->{priority},
        };

```So it appears as below, in green

```

my $conn = {
            swfurl        => "[COLOR=SeaGreen]http://www.bbc.co.uk/emp/releases/iplayer/revisions/617463_618125_4/617463_618125_4_emp.swf[/COLOR]",
            ext        => $ext,
            streamer    => $streamer,
            bitrate        => $mattribs->{bitrate},
            server        => $cattribs->{server},
            identifier    => $cattribs->{identifier},
            authstring    => $cattribs->{authString},
            priority    => $cattribs->{priority},
        };


```Seems to work ok :-)

Attached is a screenshot of how the NEW flash player looks.

---

