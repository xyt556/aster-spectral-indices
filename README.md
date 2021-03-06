# aster-spectral-indices
A dictionary-like Python object to get band ratios with ASTER images  

### TODO
Add a real ASTER granule example and plots of output

### Usage  
1. Instantiate the Indices object
        band_ratios = Indices(img)
2. Print keys to the available indices
   print(band_ratios.keys())
3. Call .get() with the desired key
   kaolinite = band_ratios.get("Kaolinite")
4. The output of .get() is a 3D numpy array
   kaolinite.shape = (1, height, width)

### Example

```Python
import numpy as np
import matplotlib.pyplot as plt
from multispectral import Indices

# Simulate a 9-layer ASTER image with 3 VNIR bands and 6 SWIR bands
img = np.random.randn(9, 1000, 1000) # (n_bands, height, width)

# Instantiate Indices dictionary
indices_dict = Indices(img)

# Get the Kaolinite index
kaolinite = indices_dict.get("Kaolinite")

# Plot the Kaolinite map
plt.imshow(kaolinite[0])

# The actual values in the dict are function objects
# A particular index can alternatively be computed by
# extracting the function from the dict and calling it
get_kaolinite_idx = indices_dict["Kaolinite"]
kaolinite = get_kaolinite_idx()

```
