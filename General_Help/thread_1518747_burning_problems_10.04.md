---
title: "burning problems 10.04"
date: 2010-06-27
forum: General Help
---

### Post by nikonfrz on 2010-06-27
seriously frustrated. cannot burn cd's...period. i tried k3b brasero, i tried permission settings, different cd brands. no avail. wtf is going on? i have read numerous posts for this and googled as much as i can and can't find a solution. i get error code 254 from k3b. never had problems till updates a month or so ago. i knock windows every chance i get and boast about ubuntu, but now all i can say is at least windows will burn a cd. if you need me to post outputs please let me know what you want. i dont burn too often but when i need to there is a reason, and it's really really frustrating :/

---

### Post by TeoBigusGeekus on 2010-06-27
Confirmed in Karmic as well. 
I spent 2 hours yesterday in my sisters pc (via teamviewer) trying to burn just one @!#$^* cd. Initially K3b gave me an error about permissions - changed them, still the same. Brasero gave an unknown error.
Tried K3b with sudo, gave me error code 254.
After googling and searching in the forums, I found out that it's an old thing that somehow resurfaced now, only the old remedies do nothing for it...

---

### Post by TeoBigusGeekus on 2010-06-27
Anyone?

---

### Post by tgm4883 on 2010-06-27
I was able to burn a cd here just fine using brasero on 10.04.

Start it from the command line, try to burn a CD, then post the command line output.

---

### Post by TeoBigusGeekus on 2010-06-27
No error message in command line, but after giving the unknown error, Brasero gives this error log:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_session_output_size
BraseroNormalize Output set (AUDIO) image = /tmp/brasero_tmp_HUIAFV.cdr
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Antonis%20Remos/03.%20%CE%95%CE%A7%CE%A9%20%CE%95%CE%A3%CE%95%CE%9D%CE%91.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize called brasero_job_set_current_action
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.089467) and gain (-7.940000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Antonis%20Remos/12.%20%CE%9C%CE%95%CE%A7%CE%A1%CE%99%20%CE%A4%CE%9F%20%CE%A4%CE%95%CE%9B%CE%9F%CE%A3%20%CE%A4%CE%9F%CE%A5%20%CE%9A%CE%9F%CE%A3%CE%9C%CE%9F%CE%A5.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.072957) and gain (-7.380000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Antonis%20Remos/Antonis%20Remos%20-%20%CE%A7%CE%B1%CE%BC%CE%BF%CE%B3%CE%AD%CE%BB%CE%B1%CF%83%CE%B5.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.075421) and gain (-8.510000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Antonis%20Remos/Professional%20Sinnerz%20-%20Otan%20s'eixa%20prwtodei.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (0.985235) and gain (-4.740000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Thanos%20Petrelis/5.petrelis123.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.016902) and gain (-7.370000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Antonis%20Remos/Antonis%20Remos%20-%20Tremo.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.063602) and gain (-8.530000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Despoina%20Vandi/Despoina%20Vandi%20-%20Akatamaxiti%20Elksi.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.049820) and gain (-7.570000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Michalis%20Xatzigiannis/Michalis%20Xatzigiannis%20-%20Gia%20Sena.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.084487) and gain (-7.360000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Gonidis%20stamatis%20-%20Ola%20s'agapane.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.042080) and gain (-4.690000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Despoina%20Vandi/Despoina%20Vandi%20-%20%CE%A3%CF%84%CE%B7%CE%BD%20%CE%B1%CF%85%CE%BB%CE%AE%20%CF%84%CE%BF%CF%85%20%CF%80%CE%B1%CF%81%CE%B1%CE%B4%CE%B5%CE%AF%CF%83%CE%BF%CF%85.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.120154) and gain (-7.840000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Michalis%20Xatzigiannis/Mixalis%20Xatzigiannis%20-%20Xeria%20psila.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.077782) and gain (-7.960000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Michalis%20Xatzigiannis/Mixalis%20Xatzigiannis%20-%20Pio%20Poli_(June%202007).ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.058832) and gain (-6.480000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Giannis%20Ploutarxos/Giannis%20Ploutarhos%20-%20File.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.060175) and gain (-8.680000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Dimitris%20Mitropanos/Dimitris%20Mitropanos%20&%20Lakis%20Papadopoulos%20-%20Gia%20Na%20Se%20Ekdikitho.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.084924) and gain (-9.060000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Elli%20Kokkinou/Elli%20Kokkinou%20-%20Htan%20Psema.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.185193) and gain (-9.560000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Elli%20Kokkinou/Elli%20Kokkinou%20-%20Kosmotheoria.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.153795) and gain (-8.960000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Elli%20Kokkinou/Elli%20Kokkinou-Tha%20perimenw.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.067517) and gain (-8.820000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Elli%20Kokkinou/Elli%20Kokkinou%20-%20Na%20Me%20Prosexeis.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.134522) and gain (-9.420000)
BraseroNormalize Analysing track file:///media/disk/My%20Shared%20Folder/ELLINIKA/Elli%20Kokkinou/Elli%20Kokkinou%20-%20Talento.ogg
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (1.122962) and gain (-9.740000)
BraseroNormalize Setting album peak (1.185193) and gain (-8.190000)
BraseroNormalize called brasero_job_tag_add
BraseroNormalize called brasero_job_tag_add
BraseroNormalize Finished successfully session
BraseroNormalize stopping
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode deactivating
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_session_output_size
BraseroWodim called brasero_job_get_audio_title
BraseroWodim called brasero_job_get_tracks
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_WAX7EV.inf)
BraseroWodim got track length 222484897959 16687
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_HIX7EV.inf)
BraseroWodim got track length 230870204081 17316
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_S2V7EV.inf)
BraseroWodim got track length 205583673469 15419
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_L7V7EV.inf)
BraseroWodim got track length 232960000000 17472
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_1BW7EV.inf)
BraseroWodim got track length 268617142857 20147
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_8FW7EV.inf)
BraseroWodim got track length 229459591836 17210
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_ZKW7EV.inf)
BraseroWodim got track length 257671836734 19326
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_SPW7EV.inf)
BraseroWodim got track length 223791020408 16785
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_H9U7EV.inf)
BraseroWodim got track length 269479183673 20211
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_2DV7EV.inf)
BraseroWodim got track length 299389387755 22455
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_AIV7EV.inf)
BraseroWodim got track length 230112653061 17259
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_PMV7EV.inf)
BraseroWodim got track length 275487346938 20662
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_XRV7EV.inf)
BraseroWodim got track length 217286530612 16297
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_WWV7EV.inf)
BraseroWodim got track length 225201632653 16891
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_UIS6EV.inf)
BraseroWodim got track length 263836734693 19788
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_COS6EV.inf)
BraseroWodim got track length 248868571428 18666
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_MSS6EV.inf)
BraseroWodim got track length 276244897959 20719
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_UXS6EV.inf)
BraseroWodim got track length 256862040816 19265
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_Q2S6EV.inf)
BraseroWodim got track length 284865306122 21365
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/sr0
	speed=24
	-dao
	fs=31m
	-swab
	-audio
	-useinfo
	-text
	/tmp/brasero_tmp_WAX7EV.inf
	/tmp/brasero_tmp_HIX7EV.inf
	/tmp/brasero_tmp_S2V7EV.inf
	/tmp/brasero_tmp_L7V7EV.inf
	/tmp/brasero_tmp_1BW7EV.inf
	/tmp/brasero_tmp_8FW7EV.inf
	/tmp/brasero_tmp_ZKW7EV.inf
	/tmp/brasero_tmp_SPW7EV.inf
	/tmp/brasero_tmp_H9U7EV.inf
	/tmp/brasero_tmp_2DV7EV.inf
	/tmp/brasero_tmp_AIV7EV.inf
	/tmp/brasero_tmp_PMV7EV.inf
	/tmp/brasero_tmp_XRV7EV.inf
	/tmp/brasero_tmp_WWV7EV.inf
	/tmp/brasero_tmp_UIS6EV.inf
	/tmp/brasero_tmp_COS6EV.inf
	/tmp/brasero_tmp_MSS6EV.inf
	/tmp/brasero_tmp_UXS6EV.inf
	/tmp/brasero_tmp_Q2S6EV.inf
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 222484897959 / bytes = 0 39246336
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -7.940000 1.089467
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroWodim stderr: scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.9
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Antonis Remos/03. &#917;&#935;&#937; &#917;&#931;&#917;&#925;&#913;.ogg
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 0 = CD-DA
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'TSSTcorp'
BraseroWodim stdout: Identification : 'CDDVDW SH-S223F '
BraseroWodim stdout: Revision       : 'SB00'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0017 (Reserved/Unknown) 
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1962752 = 1916 KB
BraseroWodim stdout: FIFO size      : 32505856 = 31744 KB
BraseroWodim stderr: Speed set to 4234 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: pregap1: -1
BraseroWodim stdout: Track 01: audio   37 MB (03:42.49) no preemp copy
BraseroWodim stdout: Track 02: audio   38 MB (03:50.88) no preemp copy
BraseroWodim stdout: Track 03: audio   34 MB (03:25.58) no preemp copy
BraseroWodim stdout: Track 04: audio   39 MB (03:52.96) no preemp copy
BraseroWodim stdout: Track 05: audio   45 MB (04:28.62) no preemp copy
BraseroWodim stdout: Track 06: audio   38 MB (03:49.46) no preemp copy
BraseroWodim stdout: Track 07: audio   43 MB (04:17.68) no preemp copy
BraseroWodim stdout: Track 08: audio   37 MB (03:43.80) no preemp copy
BraseroWodim stdout: Track 09: audio   45 MB (04:29.48) no preemp copy
BraseroWodim stdout: Track 10: audio   50 MB (04:59.40) no preemp copy
BraseroWodim stdout: Track 11: audio   38 MB (03:50.12) no preemp copy
BraseroWodim stdout: Track 12: audio   46 MB (04:35.49) no preemp copy
BraseroWodim stdout: Track 13: audio   36 MB (03:37.29) no preemp copy
BraseroWodim stdout: Track 14: audio   37 MB (03:45.21) no preemp copy
BraseroWodim stdout: Track 15: audio   44 MB (04:23.84) no preemp copy
BraseroWodim stdout: Track 16: audio   41 MB (04:08.88) no preemp copy
BraseroWodim stdout: Track 17: audio   46 MB (04:36.25) no preemp copy
BraseroWodim stdout: Track 18: audio   43 MB (04:16.86) no preemp copy
BraseroWodim stdout: Track 19: audio   47 MB (04:44.86) no preemp copy
BraseroWodim stdout: Total size:      793 MB (78:39.20) = 353940 sectors
BraseroWodim stdout: Lout start:      794 MB (78:41/15) = 353940 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type B, low Beta category (B-) (4)
BraseroWodim stdout:   ATIP start of lead in:  -11607 (97:27/18)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 18
BraseroWodim stdout: Manufacturer: Plasmon Data systems Ltd.
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 5909
BraseroWodim stdout: Starting to write CD/DVD at speed  24.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: SAO startsec: -11607
BraseroWodim stdout: Writing lead-in...
BraseroWodim stdout: Lead-in write time:   20.727s
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of   37 MB written.
BraseroWodim stdout: Track 01:    1 of   37 MB written (fifo  99%) [buf 100%]  20.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of   37 MB written (fifo 100%) [buf 100%]  21.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of   37 MB written (fifo  99%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of   37 MB written (fifo 100%) [buf 100%]  21.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of   37 MB written (fifo  99%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of   37 MB written (fifo 100%) [buf 100%]  21.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 39246336 bytes (= 39246336 ns)
=> padding 1488 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 464 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 230870204081 / bytes = 0 40725504
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -7.380000 1.072957
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Antonis Remos/12. &#924;&#917;&#935;&#929;&#921; &#932;&#927; &#932;&#917;&#923;&#927;&#931; &#932;&#927;&#933; &#922;&#927;&#931;&#924;&#927;&#933;.ogg
BraseroWodim stdout: Track 01:    7 of   37 MB written (fifo  99%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of   37 MB written (fifo 100%) [buf 100%]  21.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of   37 MB written (fifo 100%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of   37 MB written (fifo  99%) [buf 100%]  21.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of   37 MB written (fifo 100%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of   37 MB written (fifo 100%) [buf 100%]  21.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of   37 MB written (fifo  99%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of   37 MB written (fifo 100%) [buf 100%]  21.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of   37 MB written (fifo 100%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of   37 MB written (fifo 100%) [buf 100%]  22.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of   37 MB written (fifo  99%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   18 of   37 MB written (fifo 100%) [buf 100%]  22.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   19 of   37 MB written (fifo 100%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   20 of   37 MB written (fifo  99%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   21 of   37 MB written (fifo 100%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   22 of   37 MB written (fifo 100%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   23 of   37 MB written (fifo 100%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   24 of   37 MB written (fifo 100%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   25 of   37 MB written (fifo 100%) [buf 100%]  23.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   26 of   37 MB written (fifo 100%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   27 of   37 MB written (fifo  99%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   28 of   37 MB written (fifo 100%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   29 of   37 MB written (fifo 100%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   30 of   37 MB written (fifo 100%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   31 of   37 MB written (fifo 100%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   32 of   37 MB written (fifo  99%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   33 of   37 MB written (fifo  99%) [buf 100%]  23.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   34 of   37 MB written (fifo 100%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   35 of   37 MB written (fifo  99%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   36 of   37 MB written (fifo 100%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   37 of   37 MB written (fifo  99%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01: Total bytes read/written: 39247824/39247824 (16687 sectors).
BraseroWodim stdout: Starting new track at sector: 16687
BraseroWodim stdout: 
BraseroWodim stdout: Track 02:    0 of   38 MB written.
BraseroWodim stdout: Track 02:    1 of   38 MB written (fifo  99%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:    2 of   38 MB written (fifo 100%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:    3 of   38 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:    4 of   38 MB written (fifo 100%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:    5 of   38 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:    6 of   38 MB written (fifo  99%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:    7 of   38 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 40725504 bytes (= 40725504 ns)
=> padding 1728 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 192 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 205583673469 / bytes = 0 36264960
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -8.510000 1.075421
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroWodim stdout: Track 02:    8 of   38 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Antonis Remos/Antonis Remos - &#935;&#945;&#956;&#959;&#947;&#941;&#955;&#945;&#963;&#949;.ogg
BraseroWodim stdout: Track 02:    9 of   38 MB written (fifo  99%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   10 of   38 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   11 of   38 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   12 of   38 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   13 of   38 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   14 of   38 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   15 of   38 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   16 of   38 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   17 of   38 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   18 of   38 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   19 of   38 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   20 of   38 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   21 of   38 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   22 of   38 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   23 of   38 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   24 of   38 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   25 of   38 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   26 of   38 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   27 of   38 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   28 of   38 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   29 of   38 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   30 of   38 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   31 of   38 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   32 of   38 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   33 of   38 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   34 of   38 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   35 of   38 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   36 of   38 MB written (fifo  99%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   37 of   38 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02:   38 of   38 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 02: Total bytes read/written: 40727232/40727232 (17316 sectors).
BraseroWodim stdout: Starting new track at sector: 34003
BraseroWodim stdout: 
BraseroWodim stdout: Track 03:    0 of   34 MB written.
BraseroWodim stdout: Track 03:    1 of   34 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:    2 of   34 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:    3 of   34 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 36264960 bytes (= 36264960 ns)
=> padding 528 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 16 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 232960000000 / bytes = 0 41094144
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -4.740000 0.985235
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Antonis Remos/Professional Sinnerz - Otan s'eixa prwtodei.ogg
BraseroWodim stdout: Track 03:    4 of   34 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:    5 of   34 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:    6 of   34 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:    7 of   34 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:    8 of   34 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:    9 of   34 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   10 of   34 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   11 of   34 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   12 of   34 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   13 of   34 MB written (fifo 100%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   14 of   34 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   15 of   34 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   16 of   34 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   17 of   34 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   18 of   34 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   19 of   34 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   20 of   34 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   21 of   34 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   22 of   34 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   23 of   34 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   24 of   34 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   25 of   34 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   26 of   34 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   27 of   34 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   28 of   34 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   29 of   34 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   30 of   34 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   31 of   34 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   32 of   34 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   33 of   34 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03:   34 of   34 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 03: Total bytes read/written: 36265488/36265488 (15419 sectors).
BraseroWodim stdout: Starting new track at sector: 49422
BraseroWodim stdout: 
BraseroWodim stdout: Track 04:    0 of   39 MB written.
BraseroWodim stdout: Track 04:    1 of   39 MB written (fifo  99%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:    2 of   39 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:    3 of   39 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:    4 of   39 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:    5 of   39 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:    6 of   39 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:    7 of   39 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:    8 of   39 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 41094144 bytes (= 41094144 ns)
=> padding 0 bytes
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 268617142857 / bytes = 0 47384064
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -7.370000 1.016902
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Thanos Petrelis/5.petrelis123.ogg
BraseroWodim stdout: Track 04:    9 of   39 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   10 of   39 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   11 of   39 MB written (fifo 100%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   12 of   39 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   13 of   39 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   14 of   39 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   15 of   39 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   16 of   39 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   17 of   39 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   18 of   39 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   19 of   39 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   20 of   39 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   21 of   39 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   22 of   39 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   23 of   39 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   24 of   39 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   25 of   39 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   26 of   39 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   27 of   39 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   28 of   39 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   29 of   39 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   30 of   39 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   31 of   39 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   32 of   39 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   33 of   39 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   34 of   39 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   35 of   39 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   36 of   39 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   37 of   39 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   38 of   39 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04:   39 of   39 MB written (fifo  99%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 04: Total bytes read/written: 41094144/41094144 (17472 sectors).
BraseroWodim stdout: Starting new track at sector: 66894
BraseroWodim stdout: 
BraseroWodim stdout: Track 05:    0 of   45 MB written.
BraseroWodim stdout: Track 05:    1 of   45 MB written (fifo  99%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:    2 of   45 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:    3 of   45 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:    4 of   45 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:    5 of   45 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:    6 of   45 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:    7 of   45 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:    8 of   45 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:    9 of   45 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   10 of   45 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   11 of   45 MB written (fifo 100%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   12 of   45 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   13 of   45 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   14 of   45 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 47384064 bytes (= 47384064 ns)
=> padding 1680 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 144 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 229459591836 / bytes = 0 40476672
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -8.530000 1.063602
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Antonis Remos/Antonis Remos - Tremo.ogg
BraseroWodim stdout: Track 05:   15 of   45 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   16 of   45 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   17 of   45 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   18 of   45 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   19 of   45 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   20 of   45 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   21 of   45 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   22 of   45 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   23 of   45 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   24 of   45 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   25 of   45 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   26 of   45 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   27 of   45 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   28 of   45 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   29 of   45 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   30 of   45 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   31 of   45 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   32 of   45 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   33 of   45 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   34 of   45 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   35 of   45 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   36 of   45 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   37 of   45 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   38 of   45 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   39 of   45 MB written (fifo  99%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   40 of   45 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   41 of   45 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   42 of   45 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   43 of   45 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   44 of   45 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05:   45 of   45 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 05: Total bytes read/written: 47385744/47385744 (20147 sectors).
BraseroWodim stdout: Starting new track at sector: 87041
BraseroWodim stdout: 
BraseroWodim stdout: Track 06:    0 of   38 MB written.
BraseroWodim stdout: Track 06:    1 of   38 MB written (fifo  99%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:    2 of   38 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:    3 of   38 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:    4 of   38 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:    5 of   38 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:    6 of   38 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:    7 of   38 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 40476672 bytes (= 40476672 ns)
=> padding 1248 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 224 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 257671836734 / bytes = 0 45453312
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -7.570000 1.049820
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Despoina Vandi/Despoina Vandi - Akatamaxiti Elksi.ogg
BraseroWodim stdout: Track 06:    8 of   38 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:    9 of   38 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   10 of   38 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   11 of   38 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   12 of   38 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   13 of   38 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   14 of   38 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   15 of   38 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   16 of   38 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   17 of   38 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   18 of   38 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   19 of   38 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   20 of   38 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   21 of   38 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   22 of   38 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   23 of   38 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   24 of   38 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   25 of   38 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   26 of   38 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   27 of   38 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   28 of   38 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   29 of   38 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   30 of   38 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   31 of   38 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   32 of   38 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   33 of   38 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   34 of   38 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   35 of   38 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   36 of   38 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   37 of   38 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06:   38 of   38 MB written (fifo  99%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 06: Total bytes read/written: 40477920/40477920 (17210 sectors).
BraseroWodim stdout: Starting new track at sector: 104251
BraseroWodim stdout: 
BraseroWodim stdout: Track 07:    0 of   43 MB written.
BraseroWodim stdout: Track 07:    1 of   43 MB written (fifo  99%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:    2 of   43 MB written (fifo  99%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:    3 of   43 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:    4 of   43 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:    5 of   43 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:    6 of   43 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:    7 of   43 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:    8 of   43 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:    9 of   43 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   10 of   43 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   11 of   43 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   12 of   43 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 45453312 bytes (= 45453312 ns)
=> padding 1440 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 416 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 223791020408 / bytes = 0 39476736
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -7.360000 1.084487
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Michalis Xatzigiannis/Michalis Xatzigiannis - Gia Sena.ogg
BraseroWodim stdout: Track 07:   13 of   43 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   14 of   43 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   15 of   43 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   16 of   43 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   17 of   43 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   18 of   43 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   19 of   43 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   20 of   43 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   21 of   43 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   22 of   43 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   23 of   43 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   24 of   43 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   25 of   43 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   26 of   43 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   27 of   43 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   28 of   43 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   29 of   43 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   30 of   43 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   31 of   43 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   32 of   43 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   33 of   43 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   34 of   43 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   35 of   43 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   36 of   43 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   37 of   43 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   38 of   43 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   39 of   43 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   40 of   43 MB written (fifo  99%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   41 of   43 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   42 of   43 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07:   43 of   43 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 07: Total bytes read/written: 45454752/45454752 (19326 sectors).
BraseroWodim stdout: Starting new track at sector: 123577
BraseroWodim stdout: 
BraseroWodim stdout: Track 08:    0 of   37 MB written.
BraseroWodim stdout: Track 08:    1 of   37 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:    2 of   37 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:    3 of   37 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:    4 of   37 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:    5 of   37 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:    6 of   37 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 39476736 bytes (= 39476736 ns)
=> padding 1584 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 48 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 269479183673 / bytes = 0 47536128
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -4.690000 1.042080
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Gonidis stamatis - Ola s'agapane.ogg
BraseroWodim stdout: Track 08:    7 of   37 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:    8 of   37 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:    9 of   37 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   10 of   37 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   11 of   37 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   12 of   37 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   13 of   37 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   14 of   37 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   15 of   37 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   16 of   37 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   17 of   37 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   18 of   37 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   19 of   37 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   20 of   37 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   21 of   37 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   22 of   37 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   23 of   37 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   24 of   37 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   25 of   37 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   26 of   37 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   27 of   37 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   28 of   37 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   29 of   37 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   30 of   37 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   31 of   37 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   32 of   37 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   33 of   37 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   34 of   37 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   35 of   37 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   36 of   37 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08:   37 of   37 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 08: Total bytes read/written: 39478320/39478320 (16785 sectors).
BraseroWodim stdout: Starting new track at sector: 140362
BraseroWodim stdout: 
BraseroWodim stdout: Track 09:    0 of   45 MB written.
BraseroWodim stdout: Track 09:    1 of   45 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:    2 of   45 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:    3 of   45 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:    4 of   45 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:    5 of   45 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:    6 of   45 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:    7 of   45 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:    8 of   45 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:    9 of   45 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   10 of   45 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   11 of   45 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   12 of   45 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   13 of   45 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   14 of   45 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 47536128 bytes (= 47536128 ns)
=> padding 144 bytes
BraseroTranscode written 144 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 299389387755 / bytes = 0 52812288
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -7.840000 1.120154
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Despoina Vandi/Despoina Vandi - &#931;&#964;&#951;&#957; &#945;&#965;&#955;&#942; &#964;&#959;&#965; &#960;&#945;&#961;&#945;&#948;&#949;&#943;&#963;&#959;&#965;.ogg
BraseroWodim stdout: Track 09:   15 of   45 MB written (fifo 100%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   16 of   45 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   17 of   45 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   18 of   45 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   19 of   45 MB written (fifo 100%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   20 of   45 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   21 of   45 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   22 of   45 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   23 of   45 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   24 of   45 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   25 of   45 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   26 of   45 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   27 of   45 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   28 of   45 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   29 of   45 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   30 of   45 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   31 of   45 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   32 of   45 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   33 of   45 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   34 of   45 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   35 of   45 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   36 of   45 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   37 of   45 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   38 of   45 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   39 of   45 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   40 of   45 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   41 of   45 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   42 of   45 MB written (fifo  99%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   43 of   45 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   44 of   45 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09:   45 of   45 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 09: Total bytes read/written: 47536272/47536272 (20211 sectors).
BraseroWodim stdout: Starting new track at sector: 160573
BraseroWodim stdout: 
BraseroWodim stdout: Track 10:    0 of   50 MB written.
BraseroWodim stdout: Track 10:    1 of   50 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:    2 of   50 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:    3 of   50 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:    4 of   50 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:    5 of   50 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:    6 of   50 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:    7 of   50 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:    8 of   50 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:    9 of   50 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   10 of   50 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   11 of   50 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   12 of   50 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   13 of   50 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   14 of   50 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   15 of   50 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   16 of   50 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   17 of   50 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   18 of   50 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   19 of   50 MB written (fifo 100%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 52812288 bytes (= 52812288 ns)
=> padding 1872 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 336 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 230112653061 / bytes = 0 40591872
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -7.960000 1.077782
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Michalis Xatzigiannis/Mixalis Xatzigiannis - Xeria psila.ogg
BraseroWodim stdout: Track 10:   20 of   50 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   21 of   50 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   22 of   50 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   23 of   50 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   24 of   50 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   25 of   50 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   26 of   50 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   27 of   50 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   28 of   50 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   29 of   50 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   30 of   50 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   31 of   50 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   32 of   50 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   33 of   50 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   34 of   50 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   35 of   50 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   36 of   50 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   37 of   50 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   38 of   50 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   39 of   50 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   40 of   50 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   41 of   50 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   42 of   50 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   43 of   50 MB written (fifo  99%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   44 of   50 MB written (fifo 100%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   45 of   50 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   46 of   50 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   47 of   50 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   48 of   50 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   49 of   50 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10:   50 of   50 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 10: Total bytes read/written: 52814160/52814160 (22455 sectors).
BraseroWodim stdout: Starting new track at sector: 183028
BraseroWodim stdout: 
BraseroWodim stdout: Track 11:    0 of   38 MB written.
BraseroWodim stdout: Track 11:    1 of   38 MB written (fifo  99%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:    2 of   38 MB written (fifo  99%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:    3 of   38 MB written (fifo 100%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:    4 of   38 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:    5 of   38 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:    6 of   38 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:    7 of   38 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 40591872 bytes (= 40591872 ns)
=> padding 1296 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 272 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 275487346938 / bytes = 0 48595968
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -6.480000 1.058832
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroWodim stdout: Track 11:    8 of   38 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Michalis Xatzigiannis/Mixalis Xatzigiannis - Pio Poli_(June 2007).ogg
BraseroWodim stdout: Track 11:    9 of   38 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   10 of   38 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   11 of   38 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   12 of   38 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   13 of   38 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   14 of   38 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   15 of   38 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   16 of   38 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   17 of   38 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   18 of   38 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   19 of   38 MB written (fifo 100%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   20 of   38 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   21 of   38 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   22 of   38 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   23 of   38 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   24 of   38 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   25 of   38 MB written (fifo 100%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   26 of   38 MB written (fifo  99%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   27 of   38 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   28 of   38 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   29 of   38 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   30 of   38 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   31 of   38 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   32 of   38 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   33 of   38 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   34 of   38 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   35 of   38 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   36 of   38 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   37 of   38 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11:   38 of   38 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 11: Total bytes read/written: 40593168/40593168 (17259 sectors).
BraseroWodim stdout: Starting new track at sector: 200287
BraseroWodim stdout: 
BraseroWodim stdout: Track 12:    0 of   46 MB written.
BraseroWodim stdout: Track 12:    1 of   46 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:    2 of   46 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:    3 of   46 MB written (fifo 100%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:    4 of   46 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:    5 of   46 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:    6 of   46 MB written (fifo  99%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:    7 of   46 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:    8 of   46 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:    9 of   46 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   10 of   46 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   11 of   46 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   12 of   46 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   13 of   46 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   14 of   46 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   15 of   46 MB written (fifo 100%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 48595968 bytes (= 48595968 ns)
=> padding 1056 bytes
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 512 bytes for padding
BraseroTranscode written 32 bytes for padding
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode linked to BraseroWodim
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 217286530612 / bytes = 0 38329344
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode Found audio levels tags
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode New pad
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Sending audio levels tags
BraseroTranscode Set volume level -8.680000 1.060175
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode Retrieving tags
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode start piping /media/disk/My Shared Folder/ELLINIKA/Giannis Ploutarxos/Giannis Ploutarhos - File.ogg
BraseroWodim stdout: Track 12:   16 of   46 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   17 of   46 MB written (fifo 100%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   18 of   46 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   19 of   46 MB written (fifo 100%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   20 of   46 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   21 of   46 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   22 of   46 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   23 of   46 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   24 of   46 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   25 of   46 MB written (fifo  99%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   26 of   46 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   27 of   46 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   28 of   46 MB written (fifo  99%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   29 of   46 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   30 of   46 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   31 of   46 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   32 of   46 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   33 of   46 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   34 of   46 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   35 of   46 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   36 of   46 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   37 of   46 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   38 of   46 MB written (fifo  99%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   39 of   46 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   40 of   46 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   41 of   46 MB written (fifo  99%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   42 of   46 MB written (fifo 100%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   43 of   46 MB written (fifo  99%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   44 of   46 MB written (fifo  99%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 12:   45 of   46 MB written (fifo  99%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 03 5F 0E 00 00 07 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x0 No Additional Sense, Segment 11
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 201.341s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 12:   46 of   46 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 48580560 bytes
BraseroWodim stdout: Writing  time:  380.572s
BraseroWodim stdout: Average write speed  13.1x.
BraseroWodim stdout: Min drive buffer fill was 100%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    0.343s
BraseroWodim stderr: wodim: fifo had 8685 puts and 8191 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: wodim: fifo was 0 times empty and 4451 times full, min fill was 98%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroTranscode stopping
BraseroTranscode disconnecting BraseroTranscode from BraseroWodim
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
Session error : unknown (brasero_burn_record brasero-burn.c:2811)
```

---

### Post by ihavenoname on 2010-06-28
I have the same problem :(.

---

### Post by nikonfrz on 2010-06-30
anything i've had a problem for...search forums to find a fix..not this. idk. i have a 64 bit emachine laptop and never had issues with anything besides wireless. i dont know why everyone isn't having a problem with this, or why there are so few post's. ohh fyi...BUMP!

---

### Post by tgm4883 on 2010-06-30
Is everybody having this issue when trying to burn MP3's or is it any file?

---

### Post by jimmers on 2010-06-30
I have no problems burning CD'S or DVD's with K3B or Brasero in Lucid, in fact K3B is the better of the two, this may not be of any use to you, but when I do a re-install the first Programmes I install are K9Copy, Kaffeine, Gxine and K3B and Ubuntu-Restricted-Extras, and LibDvdCss2, then restart.

As said this may or not help, but try removing offending programmes and then re-install.

Luck

---

### Post by TeoBigusGeekus on 2010-06-30
The problem occurred to my sister's pc somewhere during last week. She'd been using K3b without any problem before. Some updates have probably caused it...

---

### Post by snapback77 on 2010-06-30
I had the same problem trying to burn a CD with Brasero from my FLAC files.  I had to convert them first to WAV and then burn them.  Is there any way to have the file names appear on the CD too?

---

### Post by milind_21_03 on 2010-07-03
Even I am having problem burning DVDs in Ubuntu 10.04LTS.

I was able to burn iso CDs and a few Data DVDs using Brasero. Burning CDs was flawless, but for DVDs, the file and folder names were truncated and Capitalized. :(

For some other Data DVDs there was burn error. For these compressing the files and folders to .7z worked well at times & failed at other.:confused:

Now, I am facing the problem of burning iso DVDs. Brasero exits with error log, and K3B gives error 254. For the past 5 days I've been searching for solution, but no success till now.:mad:

I don't want to switch back to Windows, grateful if anybody could help.:D

---

