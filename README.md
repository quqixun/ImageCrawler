# Image Crawler

Crawl images from baidu, bing, google (**BBG**)  
according to keyword using browser.

## 1. Install Dependencies

**1.1** Create virtual environment using conda.  
Only test in Python 3.6 and 3.7.
```shell
conda create --name crawler python=3.7
source activate crawler
```

**1.2** Download browser driver for [selenium](https://github.com/SeleniumHQ/selenium).  
Find and download the driver of the browser you use.  
https://www.seleniumhq.org/download/

**1.3** Add the driver's folder's path to ***SYSTEM PATH***.

## 2. Get Code

Clone the repo and install packages.
```shell
git clone https://github.com/quqixun/ImageCrawler.git
cd crawler
pip install -r requires.txt
```

Run test code to crawl my favourite pandas from **BBG**.
```shell
cd src
python panda.py
```

## 3. Explaination

- **ImageCrawler**: obtain HTTP path of desired images;
- **ImageDownloader**: download images to local directory.

```python
import os

from image_crawler import ImageCrawler
from image_downloader import ImageDownloader
```

**4 parameters** for ImageCrawler and ImageDownloader:
- **keyword**: you know, the keyword;
- **n_scroll**: number of scrolling in brower;
- **link_save_dir**: holds all links of images;
- **image_save_dir**: where to find all cute pandas.

```python
n_scroll = 5
keyword = 'panda'

link_save_dir = os.path.join('../data/links', keyword)
image_save_dir = os.path.join('../data/images', keyword)
```

Crawl images' links using Baidu
```python
engine = 'baidu'
baidu_links_name = 'baidu_links.csv'

baidu_ic = ImageCrawler(engine)
baidu_ic.run(keyword, n_scroll)
baidu_ic.save_links(link_save_dir, baidu_links_name)
```

Crawl images' links using Bing
```python
engine = 'bing'
bing_links_name = 'bing_links.csv'

bing_ic = ImageCrawler(engine)
bing_ic.run(keyword, n_scroll)
bing_ic.save_links(link_save_dir, bing_links_name)
```

Crawl images' links using Google
```python
engine = 'google'
google_links_name = 'google_links.csv'

google_ic = ImageCrawler(engine)
google_ic.run(keyword, n_scroll)
google_ic.save_links(link_save_dir, google_links_name)
```

Download images
```python
ider = ImageDownloader(link_save_dir)
ider.run(image_save_dir)
```

## 4. Panda

Here is a panda we found.

<img src="panda.jpg" width="300">
