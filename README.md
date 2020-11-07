# jimutmap 
[![DOI](https://zenodo.org/badge/169246557.svg)](https://zenodo.org/badge/latestdoi/169246557)
[![PyPI version](https://d25lcipzij17d.cloudfront.net/badge.svg?id=py&type=6&v=1.3.5)](https://pypi.org/project/jimutmap/)
[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0) 
![Ask Me Anything !](https://img.shields.io/badge/Ask%20me-anything-1abc9c.svg)
![Open Source Love png1](https://badges.frapsoft.com/os/v1/open-source.png?v=103)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Jimut123/jimutmap/blob/master/maps_scraper.ipynb)

## Purpose 

This manually brute forces [apple-map](https://satellites.pro/#32.916485,62.578125,4). It Then scraps all the tiles (image and road mask pair) as given by the 
parameters provided by the user. This uses an API-key generated at the time of browsing the map. The api acess-key (which can be found out by selecting one tile from Apple Map, through chrome/firefox by going Developer->Network and then it is this part of the link &accessKey...dark) is valid for a period of 10-15 mins. You need to manually go to [apple-map](https://satellites.pro/#32.916485,62.578125,4), get the API access key by pressing ctrl+shift+E and going to the network area. I tried to reverse engineer this thing but couldn't. First part of the key is time in sec from 1970, but other part is some output of complex function which needs time to decipher. If anyone finds it, let me know, submit a P.R and which may make this API fully automatic.

## Some of the example images downloaded at different scales

| | | | |
|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|
| <img width="1604" src="satellite_data/1_urban_map_sat.jpeg"> | <img width="1604" src="satellite_data/1_urban_map_mask.png"> | <img width="1604" src="satellite_data/different_zoom_map.jpeg">|<img width="1604" src="satellite_data/different_zoom_mask.png">|
|<img width="1604" src="satellite_data/higher_scale_map.jpeg">  |  <img width="1604" src="satellite_data/higher_scale_mask.png">|<img width="1604" src="satellite_data/map_us_1.jpeg">|<img width="1604" src="satellite_data/mask_us_1.png">|
|<img width="1604" src="satellite_data/raj_map_1.jpeg">  |  <img width="1604" src="satellite_data/raj_mask_1.png">|<img width="1604" src="satellite_data/us_1_map.jpeg">|<img width="1604" src="satellite_data/us_1_mask.png">|

## YouTube video 

If you are confused with the documentation, please see this video, to see the scraping in action [Apple Maps API to get enormous amount of satellite data for free using Python3](https://www.youtube.com/watch?v=voH0qhGXfsU).



## Installation

```
sudo pip install jimutmap
```

## Sample of the images downloaded

<center>
<a href="https://www.youtube.com/watch?v=wCbZhtWe72w" alt="yt video" target="_blank"><img src="satellite_data/scrn.png" alt="img of sat dat" width=85% height=85%></a>
</center>


## Need for scraping satellite data

Well it's good (best in the world) satellite images, we just need to give the coordinates (Lat,Lon, and zoom) to get your dataset
of high resolution satellite images! Create your own dataset and apply ML algorithms :')



The scraping API is present, call it and download it.
```python
>>from jimutmap import api
>>a=api('&api-access-key',min_lat_deg,max_lat_deg,min_lon_deg,max_lon_deg,zoom=19,verbose=False,threads_=110)

# Change the access key here
# give the (min_lat,max_lat,min_lon,max_lon,access_key) in this function
# note the access key is manually changed all the time here!

>>a.download()

100%|██████████████████████████████████████████████████████████████                     | 1000/10000000 [00:02<00:00, 3913.19it/s

```

#### Perks 

Well I'm not that bad. This is done through parallel proccessing, so this will take all the thread in your CPU, change the 
code to your own requirements! This is done so that you could download about **40K** images in **30 mins!** (That's too fast!!!)

Do this :

```
$ mkdir satellite_data
$ mv *.jpeg satellite_data
```

Please move this data after every fetch request done! Else you won't get the updated information (tiles) of satellite data after
that tile. It is calculated automatically so that all the progress remains saved!

#### Additional Note
This also uses multithreading, which may overload your computer, so set the parameters in the API, minimise the pool else your PC may hang! 
**This is created for educational and research purposes only! The author is not liable for any damage to private property.**

## [LICENSE](https://github.com/Jimut123/jimutmap/blob/master/LICENSE)
```
 GNU GENERAL PUBLIC LICENSE
                       Version 3, 29 June 2007

 Copyright (C) 2019-20 Jimut Bahan Pal, <https://jimut123.github.io/>
 Everyone is permitted to copy and distribute verbatim copies
 of this license document, but changing it is not allowed.
```

# BibTeX and citations

```
@misc{jimutmap_2019,
  author = {Jimut Bahan Pal},
  title = {jimutmap},
  year = {2019},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/Jimut123/jimutmap}},
}
```



