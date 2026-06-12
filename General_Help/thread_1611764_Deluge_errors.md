---
title: "Deluge errors"
date: 2010-11-02
forum: General Help
---

### Post by Karakh on 2010-11-02
I have Deluged 1.3.0-2 running on a headless Ubuntu server 10.10 box (EXT4) that I access via the deluge client on other machines on my local network, and torrents are (seemingly) stopping at random. All torrents download fine after a re-check.

Is there any kind of workaround that could perform a re-check after an error?

I've run out of ideas. Any help would be appreciated.

Relevant deluge log:
```
[DEBUG   ] 12:37:46 torrentmanager:943 on_alert_save_resume_data
[DEBUG   ] 12:37:46 torrentmanager:943 on_alert_save_resume_data
[DEBUG   ] 12:37:46 torrentmanager:943 on_alert_save_resume_data
[DEBUG   ] 12:37:46 torrentmanager:943 on_alert_save_resume_data
[DEBUG   ] 12:37:46 torrentmanager:943 on_alert_save_resume_data
[DEBUG   ] 12:37:46 torrentmanager:687 Opening torrents fastresume file for load.
[WARNING ] 12:37:46 torrentmanager:693 Unable to load fastresume file: [Errno 2] No such file or directory: '/home/kris/.config/deluge/state/torrents.fastresume'
[DEBUG   ] 12:37:46 torrentmanager:727 Saving fastresume file: /home/kris/.config/deluge/state/torrents.fastresume
[WARNING ] 12:37:46 torrentmanager:734 Error trying to save fastresume file
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 tracker_announce_alert: Linux CBT (http://inferno.demonoid.com:3413/announce) sending announce (stopped)
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 file_error_alert: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 alertmanager:123 torrent_paused_alert: Linux CBT paused
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:876 on_alert_tracker_announce
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:1011 on_alert_file_error: Linux CBT file (/home/kris/downloading/Linux CBT/CBT Nuggets Linux+ (Linux Plus) [2of2].iso) error: No such file or directory
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 torrentmanager:827 on_alert_torrent_paused
[DEBUG   ] 12:37:47 torrent:346 set_state_based_on_ltstate: Downloading
[DEBUG   ] 12:37:47 torrent:347 session.is_paused: False
[DEBUG   ] 12:37:47 alertmanager:123 save_resume_data_alert: Linux CBT resume data generated
[DEBUG   ] 12:37:47 torrentmanager:943 on_alert_save_resume_data
[DEBUG   ] 12:37:47 torrentmanager:687 Opening torrents fastresume file for load.
[WARNING ] 12:37:47 torrentmanager:693 Unable to load fastresume file: [Errno 2] No such file or directory: '/home/kris/.config/deluge/state/torrents.fastresume'
[DEBUG   ] 12:37:47 torrentmanager:727 Saving fastresume file: /home/kris/.config/deluge/state/torrents.fastresume
[WARNING ] 12:37:47 torrentmanager:734 Error trying to save fastresume file
[DEBUG   ] 12:37:47 alertmanager:123 tracker_reply_alert: Linux CBT (http://inferno.demonoid.com:3413/announce) received peers: 0
[DEBUG   ] 12:37:47 torrentmanager:859 on_alert_tracker_reply: Linux CBT (http://inferno.demonoid.com:3413/announce) received peers: 0
[DEBUG   ] 12:38:36 torrentmanager:647 Saving torrent state file.
[WARNING ] 12:38:36 torrentmanager:655 Unable to save state file.
```

---

