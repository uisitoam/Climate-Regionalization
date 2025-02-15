# Climate-Regionalization

This project is based on the use of machine learning models to improve the statistical regionalization in areas of complex topography. This technique aims to enhance the relatively poor performance of global climate models in rugged terrains or coastal areas, which do not account for local characteristics. Dynamic simulations executed by The University of La Laguna's Earth and Atmosphere Observation Group will be used for this project in an attempt to emulate them with the developed models.

Convolutional neural networks will be used in order to take into account the non-linear behavior showed in precipitation description; this networks also yield positive outcomes for describing temperature. Following this approach, two similar models will be developed to describe the mentioned variables based on synoptic condictions.

Models will be trained with Era 5 reanalysis data, using 5 predictors at 3 different pressure levels. Using only land data for this purpose (rather than land and sea data) has shown better results in this particular study. Predictions are obtained using Era 5 reanalysis data, along with 3 different GCMs: GFDL, IPSL and MIROC. Moreover, future predictions are made with data from these three models, for the periods 2030-2059 and 2070-2099. 

## Script

The following packages are needed to execute the script: `numpy`, `matplotlib`, `tensorflow`, `scipy`, `cartopy`, `netCDF4` and `datetime`; `tqdm` is also used for enable a visual reference of the progress. The program is divided into five .py scripts:
- `reader.py`: contains the required functions to extract the usefull information from the files where the data under study is given.
- `datafunctions.py`: contains the required functions to manage conveniently the extracted information. It also contains functions to obtain some metrics used to validate the model, along with a function to compute the rainfall amount based on the paramaters of a gamma-Bernouilli distribution given by the precipitation net. Functions to manage the masked arrays used on precipitation predictions are also provided. 
- `nets.py`: contains the CNN models of temperature and precipitation, along with the loss functions used for each one of them. 
- `trainfunctions.py`: contains the functions related to train and making predictions with the models, along with the obtention of some metrics used to validate the models.
- `plots.py`: contains the functions used to make the different plots showing the results of the model. 
- `main.py`: this is the script where all functions are called and used to obtain the desired results.

There is also a `bot.py` script. It is just a telegram bot developed to shown execution time along with some metrics. It also contains a function for "pretty print". Not necessary for the execution.  

## Results

On the one hand, the plots with the results for temperature and precipitation are included. There are boxplots showing the metrics evaluated, as well as comparisons of these for the different models used for prediction. Maps showing the distribution of values of these indicators over the studied territory are also provided. Finally, comparative graphs of the mean temperature (precipitation amount) predicted by each model are shown, comparing the predictions of the GOTA WRF and the convolutional networks developed in this work (CNN) until the end of the century.

On the other hand, the trained Keras models from which the results are derived are attached. In addition, in the case of precipitation, another folder is provided with the probabilities of occurrence data obtained during training, which are necessary to make predictions about the amount of rainfall. 

The complete break down of all the data and methods used, along with the analysis of the results are show in the `main.pdf` file.
