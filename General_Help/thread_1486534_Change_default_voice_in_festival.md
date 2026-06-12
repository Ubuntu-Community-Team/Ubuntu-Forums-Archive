---
title: "Change default voice in festival"
date: 2010-05-17
forum: General Help
---

### Post by solomonson on 2010-05-17
I read [this]("http://ubuntuforums.org/showthread.php?t=677277") post and was able to get the voices working, but when I change the .festivalrc file to have (voice.select 'nitech_us_slt_arctic_hts) it seems ignored.  Am I missing something?

I also tried (set! voice_default 'nitech_us_slt_arctic_hts), but that gives errors.

Any hints?

---

### Post by cariboo on 2010-05-18
Moved from Tips & Tuts to General Help.

---

### Post by ki3456 on 2010-06-27
> **solomonson said:**
> I read [this]("http://ubuntuforums.org/showthread.php?t=677277") post and was able to get the voices working, but when I change the .festivalrc file to have (voice.select 'nitech_us_slt_arctic_hts) it seems ignored.  Am I missing something?

I also tried (set! voice_default 'nitech_us_slt_arctic_hts), but that gives errors.

Any hints?

I had the same problem. I didn't mind at the start but when I tried to pipe wave output to neroAacEnc nero recognized the wave header for default voice only.

I opened /usr/share/festival/voices.scm as super user
There is a function in there called default-voice-priority-list
originally it looked like this:

(defvar default-voice-priority-list 
  '(kal_diphone
    cmu_us_bdl_arctic_hts
    cmu_us_jmk_arctic_hts
    cmu_us_slt_arctic_hts
    cmu_us_awb_arctic_hts
;    cstr_rpx_nina_multisyn       ; restricted license (lexicon)
;    cstr_rpx_jon_multisyn       ; restricted license (lexicon)
;    cstr_edi_awb_arctic_multisyn ; restricted license (lexicon)
;    cstr_us_awb_arctic_multisyn
    ked_diphone
    don_diphone
    rab_diphone
    en1_mbrola
    us1_mbrola
    us2_mbrola
    us3_mbrola
    gsw_diphone  ;; not publically distributed
    el_diphone
    )
  "default-voice-priority-list
   List of voice names. The first of them available becomes the default voice.")

I added my preferred voice and saved:

(defvar default-voice-priority-list 
  '(nitech_us_slt_arctic_hts
    kal_diphone
    cmu_us_bdl_arctic_hts
    cmu_us_jmk_arctic_hts
    cmu_us_slt_arctic_hts
    cmu_us_awb_arctic_hts
;    cstr_rpx_nina_multisyn       ; restricted license (lexicon)
;    cstr_rpx_jon_multisyn       ; restricted license (lexicon)
;    cstr_edi_awb_arctic_multisyn ; restricted license (lexicon)
;    cstr_us_awb_arctic_multisyn
    ked_diphone
    don_diphone
    rab_diphone
    en1_mbrola
    us1_mbrola
    us2_mbrola
    us3_mbrola
    gsw_diphone  ;; not publically distributed
    el_diphone
    )
  "default-voice-priority-list
   List of voice names. The first of them available becomes the default voice.")

This is a  complete hack. Hope it helps.

---

### Post by solomonson on 2010-06-28
That worked for me too.  Thanks for sharing!

BTW:  Do you have any idea on how to change the speed of the voice?

---

