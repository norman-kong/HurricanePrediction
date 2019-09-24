# Climate Change AI Hackathon, September 13-15, 2019

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/kongnorman/ClimateChangeHack/master)

To do:

- Properly document everything we've done to this point.

- Fix the bias in our dataset: We have 15 channels, and so for dimensionality
reduction, we picked the second row, because the classes are ranked somewhat in ascending order, and so keeping the second row would assure we would almost always have a hurricane (1) and occasionally a normal class (-1). However, currently, we have way more hurricane images than normal images. Rather than pick the 2nd row, we should try this:

search the 15 rows of each image and keep every image that has a hurricane as a hurricane image. The rest of the images, we label as -1. The reason is to avoid false negatives (ie, a hurricane image categorized as a "normal"). The first proposed idea was to randomly select between 1 and -1 for all images that contained those numbers. My worry is that images which contain hurricanes can be classified as normal, and this would make it very hard for a model to learn what a hurrican is. Also, we should try to keep this balanced (50:50).

-> Currently, we have high accuracy scores because our dataset is extremely biased and these results are heavily influenced by chance. Once we eliminate this bias, we expect a significant decline in scores. 

- Add features beyond temperature (or just one dimension in general).

-> We expect an increase in scores after adding more features. 

- then, play around with the models. 

- eventually: multi class classification?

- eventually: using more data, training across years (ex: train on 1 year, validate on the next, then test on the next after that) - requires computing in the cloud, huge amounts of data. 

- fix binder

note on accessing the full dataset- 
Accessing the google bucket: because of GCS FUSE ("Cloud Storage FUSE is an open source FUSE adapter that allows you to mount Cloud Storage buckets as file systems on Linux or macOS systems."), can treat google buckets as files and directories. cool stuff

path: 'Users/normankong/Desktop/data'

also todo (personal thing):
check the reshape function when flattening the data for ease of manipulation:

```
# Flattening image dimensions into 1 array
samples = np.resize(samples,(772,1,884736))
print(samples.shape)
print(samples)

# Flattening temp 
samples = np.resize(samples,(772,884736))
print(samples.shape)
print(samples)
```
look into flatten function??

Authors: <br>
Norman Kong <br>
Oliver Miller
