---
title: "unable to generate square wave"
date: 2011-08-16
forum: General Help
---

### Post by ogopa on 2011-08-16
Hi, I am trying to modify the sample program pcm.c(which generates a sine wave) from the alsa website to produce a square wave.
Square wave = sign(sinusoidal wave)
So then why isn't the following code creating a square wave:
```
int sgn(double d){
  if (d>=0) d=1;
   else d=-1;
  return d;
    }

static void generate_square(const snd_pcm_channel_area_t *areas, 
                           snd_pcm_uframes_t offset,
                           int count, double *_phase)
{
    static double max_phase = 2. * M_PI;
    double phase = *_phase;
    double step = max_phase*freq/(double)rate;
    unsigned char *samples[channels];
    int steps[channels];
    unsigned int chn;
    int format_bits = snd_pcm_format_width(format);
    unsigned int maxval = (1 << (format_bits - 1)) - 1;
    int bps = format_bits / 8;  // bytes per sample 
    int phys_bps = snd_pcm_format_physical_width(format) / 8;
    int big_endian = snd_pcm_format_big_endian(format) == 1;
    int to_unsigned = snd_pcm_format_unsigned(format) == 1;
    int is_float = (format == SND_PCM_FORMAT_FLOAT_LE ||
                    format == SND_PCM_FORMAT_FLOAT_BE);
    double amplitude_scale = amplitude/8.56;


    // verify and prepare the contents of areas 
    for (chn = 0; chn < channels; chn++) {
            if ((areas[chn].first % 8) != 0) {
                    printf("areas[%i].first == %i, aborting...", chn , areas[chn].first);
                    exit(EXIT_FAILURE);
            }
            samples[chn] = (((unsigned char *)areas[chn].addr) + (areas[chn].first / 8));
           if ((areas[chn].step % 16) != 0) {
                   // printf("areas[%i].step == %i, aborting...  ", chn areas[chn].step);
                   exit(EXIT_FAILURE);
            }
            steps[chn] = areas[chn].step / 8;
            samples[chn] += offset * steps[chn];
    }
    // fill the channel areas 
    while (count-- > 0) {
            union {
                    float f;
                    int i;
            } fval;
            int res, i;
            if (is_float) {
            int a = sgn(amplitude_scale * sin(phase) * maxval);
                    fval.f = (float) a;
                    res = fval.i;
            } else { 
            int b = sgn(amplitude_scale * sin(phase) * maxval);
                    res = b;
        }
                    

            if (to_unsigned)
                    res ^= 1U << (format_bits - 1);
            for (chn = 0; chn < channels; chn++) {
                    // Generate data in native endian format 
                    if (big_endian) {
                            for (i = 0; i < bps; i++)
                                    *(samples[chn] + phys_bps - 1 - i) = (res >> i * 8) & 0xff;
                    } else {
                            for (i = 0; i < bps; i++)
                                    *(samples[chn] + i) = (res >>  i * 8) & 0xff;
                    }
                    samples[chn] += steps[chn];
            }
            phase += step;
            if (phase >= max_phase)
                    phase -= max_phase;
    }
    *_phase = phase;

}
```If I take out the sgn function from the code, it generates a sine wave. Any help would be greatly appreciated.

---

### Post by JKyleOKC on 2011-08-16
Oops...

---

### Post by Topsiho on 2011-08-16
Why don't you try it out with a simple sine function, sin(x), between let's say -10 and +10? And then you try to create your square function with sgn(sin(x))?

Why do you ask your question in the form such as you do, forcing the reader to read all those declarations, having no clue, unless maybe after much effort, what they are useful for?

My twopence :)

Topsiho

---

