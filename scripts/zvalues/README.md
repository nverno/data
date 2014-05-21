## These scripts compute altitude values (z-values)
Z-values are altitude values relative to the center of the plots.

### Method to calculate z-values
1. $z = r\cos(\theta_B) \tan(\theta_S)$, where $\theta_B$ is the angle between the slope aspect and the vector from a given point through the origin, $\theta_S$ is the slope angle. and $r$ is the distance from the origin to the point.
  * $\theta_B$ is calculated from dot product of the projection of the slope aspect onto the 2d plot, $a$, and the vector from a given point through the origin, $b$:
  * $\theta_B = cos^{-1} ( \frac{ a \cdot b } {|a||b| } )$
  * Using this method, if $\theta_B > 90^{\circ}$, then $z$ will be a negative value, ie. downslope from the center of the plot.
2. Notes
  * Due to machine precision error with the arccos function, $\frac{a \cdot b}{|a||b|}$ was rounded to 15 digits (machine precision ~ $2e-16$).  When $a \cdot b$ is very close to $|a||b|$, (i.e. they are the same in reality), the fraction is sometimes computed to be slightly greater than 1 on the machine which leads to a NAN result when passed to the arccos function in R.

### Moosilauke
* On Moosilauke, each plot has an azimuth and slope calculate along the azimuth.  Z-value are calculated from these values in addition to plant x,y coordinates.
* The y-axis is oriented in the northeast direction for Moosilauke plots.
