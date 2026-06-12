---
title: "Sound Issues in World of Warcraft"
date: 2009-06-30
forum: General Help
---

### Post by b12nd0n on 2009-06-30
Hi, I've been having trouble with my sound in Wow, aka it doesn't work at all. All my other wine programs work fine, I have ALSA (and no others) enabled, 44100 rate, 16 bits, ect.

Normally this would be something for the WoW or Wine forums; but i figured you guys might be able to help after I saw my sound log.




6/30 07:37:36.714  => Version 3.1.3 (9947) May 26 2009 
6/30 07:37:36.736    
6/30 07:37:36.737  => Setting up Game Sound: 
6/30 07:37:36.738   - SESound Engine Init 
6/30 07:37:36.739   - FMOD Memory Init 
6/30 07:37:36.740   - FMOD System Create 
6/30 07:37:36.742   - FMOD version 00040907 detected 
6/30 07:37:36.742   - Hardware is DISABLED 
6/30 07:37:36.743   - Reverb is DISABLED 
6/30 07:37:36.743   - 1 Output drivers detected 
6/30 07:37:36.744   --- [0] System Default 
6/30 07:37:36.745   -######## FMOD ERROR! (err 12) A Win32 COM related error occured. COM failed to initialize or a QueryInterface failed meaning a Windows codec or driver was not installed properly.  
6/30 07:37:36.745  .\SoundEngine.cpp(2728) 
6/30 07:37:36.746   -########################################################################################### 
6/30 07:37:36.746   -######## FMOD ERROR! (err 12) A Win32 COM related error occured. COM failed to initialize or a QueryInterface failed meaning a Windows codec or driver was not installed properly.  
6/30 07:37:36.746   -######## ERROR INITIALIZING. ALL GAME SOUND DISABLED. 
6/30 07:37:36.746  .\SoundEngine.cpp(2729) 
6/30 07:37:36.747   -########################################################################################### 
6/30 07:37:36.747  => Game Sound Init Failed. 
6/30 07:37:36.748    
6/30 07:37:36.751  => User Settings Report: 
6/30 07:37:36.752   - ========= PLAYBACK ========= 
6/30 07:37:36.752   - Enable All Sound         [1] 
6/30 07:37:36.752   - Enable SFX               [1] 
6/30 07:37:36.753   --- Enable Error Speech    [1] 
6/30 07:37:36.753   --- Enable Emote Sounds    [1] 
6/30 07:37:36.753   - Enable Music             [1] 
6/30 07:37:36.755   --- Loop Music             [0] 
6/30 07:37:36.755   - Enable Ambient Sounds    [1] 
6/30 07:37:36.756   - Sound at Character       [1] 
6/30 07:37:36.756   - Sound in Background      [0] 
6/30 07:37:36.756   - Enable Reverb            [0] 
6/30 07:37:36.756   - Enable Software HRTF     [0] 
6/30 07:37:36.758   - Sound Quality            [1] 
6/30 07:37:36.759   - 
6/30 07:37:36.759   - ========== VOLUME ========== 
6/30 07:37:36.760   - Master Volume         [1.00] 
6/30 07:37:36.760   - SFX Volume            [1.00] 
6/30 07:37:36.768   - Music Volume          [0.40] 
6/30 07:37:36.776   - Ambience Volume       [0.60] 
6/30 07:37:36.784   - 
6/30 07:37:36.792   - =========== MISC =========== 
6/30 07:37:36.800   - Sound Channels          [32] 
6/30 07:37:36.808   - Use Hardware             [0] 
6/30 07:37:36.816   - Mix Mode 2               [0] 
6/30 07:37:36.824   - DSP Buffer Size       [AUTO] 
6/30 07:37:36.832   - Armor Foley SFX (Self)   [1] 
6/30 07:37:36.833   - Armor Foley SFX (Others) [1] 
6/30 07:37:36.833  => End of User Settings Report 
6/30 07:38:02.158    
6/30 07:38:02.177  => Shutting Down Game Sound 
6/30 07:38:02.205  => Done Shutting Down Game Sound 
6/30 07:38:02.407    
6/30 07:38:02.407  => Setting up Game Sound: 
6/30 07:38:02.407   - SESound Engine Init 
6/30 07:38:02.407   - FMOD Memory Init 
6/30 07:38:02.409   - FMOD System Create 
6/30 07:38:02.410   - FMOD version 00040907 detected 
6/30 07:38:02.410   - Hardware is ENABLED 
6/30 07:38:02.410   - Reverb is DISABLED 
6/30 07:38:02.412   - 1 Output drivers detected 
6/30 07:38:02.412   --- [0] System Default 
6/30 07:38:02.414   -######## FMOD ERROR! (err 12) A Win32 COM related error occured. COM failed to initialize or a QueryInterface failed meaning a Windows codec or driver was not installed properly.  
6/30 07:38:02.414  .\SoundEngine.cpp(2728) 
6/30 07:38:02.414   -########################################################################################### 
6/30 07:38:02.415   -######## FMOD ERROR! (err 12) A Win32 COM related error occured. COM failed to initialize or a QueryInterface failed meaning a Windows codec or driver was not installed properly.  
6/30 07:38:02.415   -######## ERROR INITIALIZING. ALL GAME SOUND DISABLED. 
6/30 07:38:02.415  .\SoundEngine.cpp(2729) 
6/30 07:38:02.415   -########################################################################################### 
6/30 07:38:02.416  => Game Sound Init Failed. 
6/30 07:38:02.416    
6/30 07:38:02.421  => User Settings Report: 
6/30 07:38:02.422   - ========= PLAYBACK ========= 
6/30 07:38:02.422   - Enable All Sound         [1] 
6/30 07:38:02.423   - Enable SFX               [1] 
6/30 07:38:02.423   --- Enable Error Speech    [1] 
6/30 07:38:02.423   --- Enable Emote Sounds    [1] 
6/30 07:38:02.423   - Enable Music             [1] 
6/30 07:38:02.425   --- Loop Music             [0] 
6/30 07:38:02.425   - Enable Ambient Sounds    [1] 
6/30 07:38:02.426   - Sound at Character       [1] 
6/30 07:38:02.426   - Sound in Background      [0] 
6/30 07:38:02.427   - Enable Reverb            [0] 
6/30 07:38:02.427   - Enable Software HRTF     [0] 
6/30 07:38:02.428   - Sound Quality            [1] 
6/30 07:38:02.436   - 
6/30 07:38:02.444   - ========== VOLUME ========== 
6/30 07:38:02.452   - Master Volume         [1.00] 
6/30 07:38:02.460   - SFX Volume            [1.00] 
6/30 07:38:02.468   - Music Volume          [0.40] 
6/30 07:38:02.476   - Ambience Volume       [0.60] 
6/30 07:38:02.484   - 
6/30 07:38:02.492   - =========== MISC =========== 
6/30 07:38:02.500   - Sound Channels          [32] 
6/30 07:38:02.508   - Use Hardware             [1] 
6/30 07:38:02.516   - Mix Mode 2               [0] 
6/30 07:38:02.528   - DSP Buffer Size       [AUTO] 
6/30 07:38:02.536   - Armor Foley SFX (Self)   [1] 
6/30 07:38:02.544   - Armor Foley SFX (Others) [1] 
6/30 07:38:02.552  => End of User Settings Report 
6/30 07:38:12.621    
6/30 07:38:12.651  => Shutting Down Game Sound 
6/30 07:38:12.668  => Done Shutting Down Game Sound

---

### Post by Soul-Sing on 2009-06-30
Is this thread helpful?: [http://ubuntuforums.org/showthread.php?t=908238](http://ubuntuforums.org/showthread.php?t=908238)
or this one: [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)
==> > If you experience stuttering, bad sound or no sound what so ever, then add the following options as well: 
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"

---

